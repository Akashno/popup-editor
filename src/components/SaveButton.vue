<template>
<button class="save-button" @click="$emit('saveDesign')">Save Design
     <svg width="24" height="24" viewBox="0 0 24 24" xmlns="http://www.w3.org/2000/svg" aria-labelledby="saveIconTitle" stroke="#fff" stroke-linecap="square" fill="none" color="#fff"><path d="M17.293 3.293 21 7v13a1 1 0 0 1-1 1H4a1 1 0 0 1-1-1V4a1 1 0 0 1 1-1h12.586a1 1 0 0 1 .707.293Z"/><path d="M7 13h10v8H7zM8 3h8v5H8z"/></svg> 
    </button>
</template>

<script>
export default {
}
</script>

<style scoped>
.save-button:hover {
  background: rgb(118, 33, 236);
  font-weight: bolder;
}
.save-button {
  cursor: pointer;
  display: flex;
  font-size: 15px;
  gap: 10px;
  align-items: center;
  border: none;
  color: white;
  background: rgb(127,54,248);
  padding: 10px 10px;
  font-weight: bolder;
  bottom: 10px;
  position: absolute;
  bottom: 20px;
  right: 20px;
  border-radius: 30px;
  -webkit-box-shadow: 10px 11px 36px -13px rgba(0,0,0,0.75);
    -moz-box-shadow: 10px 11px 36px -13px rgba(0,0,0,0.75);
    box-shadow: 10px 11px 36px -13px rgba(0,0,0,0.75);
}

</style>