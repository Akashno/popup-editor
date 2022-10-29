<template>
  <div class="home">
    <PopUp/>
  </div>
</template>

<script>
// @ is an alias to /src
import PopUp from '@/components/PopUp.vue'

export default {
  name: 'HomeView',
  components: {
    PopUp,
  }
}
</script>
<style>
.home{
  max-width: 1440px;
  margin-left:auto;
  margin-right:auto;

}
body{
  padding:0px;
  margin:0px;
  background: #27272F;
}


</style>
