<template>
  <div class="container mt-5">
    <h2 class="fst-italic text-center mb-5">Rick and Morty Ejemplo</h2>
    <div class="row" >
      <div v-for="character of characters" :key="character.id" class="col-sm-12 col-md-4">
        <h3>{{character.name}}</h3> 
        <!--personaje-->
        <img :src="character.image" alt="">
        <router-link :to="`/characters/${character.id}`">Personaje</router-link>
        <p>{{ character.body }}</p>
        <button class="btn btn-secondary" @click="personaje(character.id)">Ver personaje</button>
        <hr/>
      </div>
    </div>

  </div>
</template>

<script>
// @ is an alias to /src

export default {
  name: 'HomeView',
  components: {
  },
  data() {
    return {
      characters: [],
      charactersid: [],
    }
  },
  methods: {
    async consumirCharacter() {
      try {
        const data = await fetch('https://rickandmortyapi.com/api/character');
        const getcharacter = await data.json();
        this.characters = getcharacter.results;
        console.log(this.characters)
      } catch (error) {
        console.log(error);
        throw error;
      }
    },
    
  },
  created() {
    this.consumirCharacter();
  }
}
</script>

<style scope>
h3 {
  font-size: 16px !important;
}
</style>
