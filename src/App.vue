<template>
<div id="app">
  <h1>Personajes Rick and Morty</h1>

  <div v-for="(p, i) in personajes" :key="i" class="personajes">
    <Character @toctoc="saludar" :src="p.picture" :name="p.nombre" :indice="indice" />
  </div>
</div>
</template>

<script>
import Character from "./components/Character";
export default {
  components: {
    Character,
  },
  data() {
    return {
      personajes: [],
      indice: "",
    };
  },
  
methods: {
    saludar(indice) {
      this.personajes.splice(indice, 1);
    },
  },
  mounted() {
    fetch("https://rickandmortyapi.com/api/character")
      .then((response) => response.json())
      .then((json) => {
        let data = json.results;

        data.slice(0, 10).forEach((el) => {
          let nombre = el.name;
          let picture = el.image;

          this.personajes.push({
            nombre,
            picture,
          });
        });
      })
      .catch((err) => {
        console.log(` ${err}`);
      });
  },
};
</script>
<style lang="scss">
#app {
  color: rgb(252, 0, 105);
  background-image: url(/foto.png);
  background-repeat: no-repeat;
  background-size: cover;
  text-align: center;

}
.personajes {
  border-radius: 50%;

}
</style>


