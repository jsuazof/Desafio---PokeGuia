<template>
  <div>
    <h1 class="titulo">PokeGuía</h1>
    <label for="">Pokemon:</label>
    <input type="text" v-model="pokemon.name">
    <button @click="getPokemon">Search</button>
    <div class="row d-flex justify-content-center flex-nowrap">
    <div class="col-md-6 card"  style="width: 18rem;">
      <img :src="getImage" class="card-img-top" alt="...">
      <div class="card-body">
        <h5 class="card-title">{{pokemon.name}}</h5>
      </div>
    </div>
    </div>
    <h2>Moves</h2>
    <div  v-for = "(getMove, index) in  getMoves" :key="index">
      
      <p>{{getMove.move.name}}</p>
  
    </div>
    <h2>Abilities</h2>
    <div  v-for = "(getAbility, index) in  getAbilities" :key="index">
      
      <p>{{getAbility.ability.name}}</p>
  
    </div>
    
  </div>
</template>

<script>
export default {
  // eslint-disable-next-line
  name: "Pokeapp", 
  data(){
    return{
      pokemon: {
      name: "pikachu",
      sprites:{
        front_default: "",
      },
      abilities: [],
      moves: [],
    },
    };
   
  },
 
  created() {
    this.getPokemon();
  },
  methods: {
    getPokemon() {
      fetch(`https://pokeapi.co/api/v2/pokemon/${this.pokemon.name}`)
        .then((response) => response.json())
        .then((json) => (this.pokemon = json));
    },
  },
  computed: {
    getImage() {
      return this.pokemon.sprites.other.dream_world.front_default;
    },
    getMoves() {
      return this.pokemon.moves;
    },
    getAbilities() {
      return this.pokemon.abilities;
    },
    getName() {
      return this.pokemon.name;
    },
  },
};
</script>

<style>
.titulo {
  font-size: 40px;
  margin-bottom: 20px;
}
.imagen {
  height: 250px;
}

.columna {
  display: flex;
  align-items: center;
  justify-content: flex-end;
  font-size: 25px;
  font-weight: bold;
}
.pokename {
  font-size: 30px;
  margin-top: 9px;
  font-weight: bold;
}
h2 {
  font-size: 30px;
}
</style>
