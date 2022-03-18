<template>
  <h3> {{ character.name}} </h3>
  <img :src="character.image" alt="">
  <h4> {{ character.status}} </h4>
</template>

<script>
 export default {
   data() {
     return {
       character: {}
     }
   },
   methods: {
     async mostrarCharacterPorId() {
      try {
        const data = await fetch(`https://rickandmortyapi.com/api/character/${this.$route.params.id}`);
        const getCharacterid = await data.json();
        this.character = getCharacterid;
        console.log(this.character);
      
      } catch (error) {
        console.log(error);
        throw error;
      }
     }
   },
   created() {
     this.mostrarCharacterPorId();
   }
 }
</script>

<style>

</style>