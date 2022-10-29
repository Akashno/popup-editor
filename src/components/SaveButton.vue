<template>
<button class="save-button" >Save Design
      <svg width="24" height="24" viewBox="0 0 24 24" xmlns="http://www.w3.org/2000/svg">
        <path fill-rule="evenodd" clip-rule="evenodd"
          d="M19.82 6.195c.24.26.24.683 0 .943L9.974 17.805c-.24.26-.63.26-.87 0L4.18 12.47a.707.707 0 0 1 0-.942c.24-.26.63-.26.87 0l4.488 4.861L18.95 6.195c.24-.26.63-.26.87 0Z"
          fill="white" />
      </svg>
    </button>
</template>

<script>
export default {

}
</script>

<style scoped>

.save-button:hover {
  background: #000000;
}
.save-button {
  cursor: pointer;
  display: flex;
  gap: 10px;
  align-items: center;
  border: none;
  background: #201c1c;
  color: white;
  padding: 10px 10px;
  bottom: 10px;
  font-size: 15px;
  position: fixed;
  bottom: 10px;
  right: 10px;
  border-radius: 10px;
  box-shadow: 20px 20px 50px rgb(53, 49, 49);
  border: 1px solid #F6EAE5
}

</style>