<template>
  <div class="wrapper">
    
    <!-- Side Bar -->
    <SideBar @updateBgColor="updateBgColor" @updateStarColor="updateStarColor" />
    <!-- Canvas -->
    <div class="canvas">
      <div class="circle" ref="circle">
        <div>
          <div class="stars" ref="star">
            <svg class="star" :fill="starColor" width="40" height="40" viewBox="0 0 24 24"
              xmlns="http://www.w3.org/2000/svg">
              <path
                d="M12.5 17.925 6.629 21l1.121-6.512L3 9.875l6.564-.95L12.5 3l2.936 5.925 6.564.95-4.75 4.613L18.371 21z" />
            </svg>
            <svg class="star" :fill="starColor" width="50" height="50" viewBox="0 0 24 24"
              xmlns="http://www.w3.org/2000/svg">
              <path
                d="M12.5 17.925 6.629 21l1.121-6.512L3 9.875l6.564-.95L12.5 3l2.936 5.925 6.564.95-4.75 4.613L18.371 21z" />
            </svg>
            <svg class="star" :fill="starColor" width="40" height="40" viewBox="0 0 24 24"
              xmlns="http://www.w3.org/2000/svg">
              <path
                d="M12.5 17.925 6.629 21l1.121-6.512L3 9.875l6.564-.95L12.5 3l2.936 5.925 6.564.95-4.75 4.613L18.371 21z" />
            </svg>
          </div>
          <h1 class="header" draggable="true" contenteditable="true" ondragover="allowDrop(event)">
            All the text and elements in this popup should be editable and dragable
          </h1>
          <div>
            <input class="email-input" type="text" placeholder="E-mail" draggable="true">
          </div>
          <div>
            <button class="signup-button" draggable="true" contenteditable="true">SIGNUP NOW</button>
            <p class="subHeader" contenteditable="true">No credit card required. No surprises</p>
          </div>
        </div>
      </div>
    </div>
     <!-- Save Buton -->
    <button class="save-button">Save Design
      <svg width="24" height="24" viewBox="0 0 24 24" xmlns="http://www.w3.org/2000/svg">
        <path fill-rule="evenodd" clip-rule="evenodd"
          d="M19.82 6.195c.24.26.24.683 0 .943L9.974 17.805c-.24.26-.63.26-.87 0L4.18 12.47a.707.707 0 0 1 0-.942c.24-.26.63-.26.87 0l4.488 4.861L18.95 6.195c.24-.26.63-.26.87 0Z"
          fill="white" />
      </svg>
    </button>

  </div>
</template>


<!-- Add "scoped" attribute to limit CSS to this component only -->
<script>
import SideBar from './SideBar.vue'
export default {
  components: { SideBar },
  data() {
    return {
      bgColor: "#DE795E",
      starColor: "#C85943",
    }

  },
  methods: {
    updateBgColor(color) {
      this.bgColor = color
      this.$refs.circle.style.background = this.bgColor
      this.$refs.circle.style.boxShadow = `0 0 0 8px ${this.bgColor}`
    },

    updateStarColor(color) {
      this.starColor = color
    },
    changeBackgroundColor() {
    },
  }
}
</script>
<style scoped>
.signup-button {
  margin-top: 20px;
  font-size: 25px;
  border: none;
  background: #413E41;
  color: #FEFEFD;
  width: 80%;
  padding: 15px 0px;
  border-radius: 15px;
  font-weight: 950;
}

.email-input {
  border: none;
  padding: 10px;
  background: #FEFEFD;
  width: 80%;
  padding: 15px 0px;
  text-indent: 10px;
  border-radius: 15px;
}

.header {
  max-width: 25rem;
  height: 150px;
  display: flex;
  align-items: center;
  justify-content: center;
  color: #FEFEFD;
  margin: auto;
}

.subHeader {
  color: #F6EAE5;
}

.stars {
  height: 40px;
}

.circle {
  margin: auto;
  margin-top: 20px;
  flex-grow: 1;
  justify-self: center;
  min-width: 200px;
  min-height: 200px;
  max-width: 400px;
  max-height: 400px;
  aspect-ratio: 1 / 1;
  border-radius: 50%;
  background-color: #DE795E;
  padding: 45px;
  position: relative;
  display: flex;
  justify-content: center;
  align-items: center;
  border: 4px solid #fff;
  box-shadow: 0 0 0 8px #DE795E;

}



.wrapper {
  display: flex;
}

.canvas {
  width: 100vw;
  height: 100vh;
  background: #2c2c2c;
  display: grid;
  place-content: center;

}

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
}
</style>
