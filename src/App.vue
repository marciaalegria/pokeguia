<template>
  <div id="app">
      <hijo></hijo>
  </div>
</template>

<script>
import Hijo from "./components/Hijo.vue";
  export default {
    data: function() {
      return {

      };
    },
    components : {
        'hijo': Hijo,
    }
  }
</script>

<style scoped>
  #app {
    font-size: 25px;
    font-family: "Calibri", sans-serif;
    color: rgb(84, 125, 172);
    background: rgb(245, 235, 95);
  }
</style>