<template>
  <div id="app">
    <router-view/>
  </div>
</template>

<script>
import PopUp from './components/PopUp.vue'
export default {
  components:{
    PopUp
  }
}
</script>
<style>

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

</style>
