<template>
  <div class="home">
    <PopUp/>
  </div>
</template>

<script>
// @ is an alias to /src
import PopUp from '@/components/PopUp.vue'
import DraggableDiv from '@/components/DraggableDiv.vue'

export default {
  name: 'HomeView',
  components: {
    PopUp,
    DraggableDiv
  }
}
</script>
<style>
body{
  padding:0px;
  margin:0px;
  background: #2c2c2c;
}


</style>
