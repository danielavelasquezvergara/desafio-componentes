<template>
<div>
  <img class="personajes" :src="src" alt />
  <h3 @click="avisaleApapa">{{name}} {{indice}}</h3>
</div>
</template>

<script>
export default {
  name: "Character",
  props: {
    src: String,
    name: String,
    indice: String,
  },
  methods: {
    avisaleApapa() {
      this.$emit("toctoc", this.indice);
    },
  },
};
</script>

<style>
</style>
