<template>
  <div class="wrapper">


    <!-- Side Bar -->
    <SideBar @updateBgColor="updateBgColor" @updateStarColor="updateStarColor"  />
    <!-- Canvas -->
    <div class="canvas" @drop="drop($event)" @dragover="allowDrop($event)">

      <div class="circle" ref="circle">
        <div class="drop-zone" @drop="drop($event)" @dragover="allowDrop($event)" @dragenter.prevent @dragover.prevent>
          <div class="stars  " ref="star">
            <div draggable="true" id="drag1" @dragstart="drag($event)">
             <Stars :starColor="starColor"/> 
            </div>
          </div>
          <div class="drop-zone" @drop="drop($event)" @dragover="allowDrop($event)" @dragenter.prevent
            @dragover.prevent>
            <h1 class="header " id="header" @dragstart="drag($event)" draggable="true" ref="header">
              All the text and elements in this popup should be editable and dragable
            </h1>
          </div>
          <div class="drop-zone" @drop="drop($event)" @dragover="allowDrop($event)" @dragenter.prevent @dragover.prevent>
            <input @dragstart="drag($event)" id="email-input" class="email-input " type="text" placeholder="E-mail" draggable="true">
          </div>
          <div>
            <div class="drop-zone" @drop="drop($event)" @dragover="allowDrop($event)" @dragenter.preventd @dragover.prevent>
              <button class="signup-button " @dragstart="drag($event)" id="signup-button" draggable="true">SIGNUP NOW</button>
            </div>
            <div class="drop-zone" @drop="drop($event)" @dragover="allowDrop($event)" @dragenter.prevent
              @dragover.prevent>
              <p class="subHeader " @dragstart="drag($event)" id="subHeader" draggable="true">No credit card required.
                No surprises</p>
            </div>
          </div>
        </div>
      </div>
    </div>
    <!-- Save Buton -->
    <SaveButton @click="saveDesign()" />
  </div>
</template>


<!-- Add "scoped" attribute to limit CSS to this component only -->
<script>
import SideBar from './SideBar.vue'
import Stars from './Stars.vue'
import SaveButton from './SaveButton.vue'
export default {
  components: { SideBar,Stars,SaveButton },
  data() {
    return {
      bgColor: "#DE795E",
      starColor: "#C85943",
    }

  },
  methods: {
    allowDrop(ev) {
      ev.preventDefault()
    },
    drag(ev) {
      ev.dataTransfer.setData("text", ev.target.id);
    },
    drop(ev) {
      ev.preventDefault();
      let data = ev.dataTransfer.getData("text");
      ev.target.appendChild(document.getElementById(data));
    },
    saveDesign() {
      let markup = document.getElementsByClassName('circle');
      console.log(markup)
    },
    updateBgColor(color) {
      this.bgColor = color
      this.$refs.circle.style.background = this.bgColor
      this.$refs.circle.style.boxShadow = `0 0 0 8px ${this.bgColor}`
    },
    updateStarColor(color) {
      this.starColor = color
    },
  }
}
</script>
<style scoped>
.signup-button {
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
  height: 50px;
}

.circle {
  margin-top: 20px;
  flex-grow: 1;
  justify-self: center;
  min-width: 400px;
  min-height: 400px;
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
  background: #1A1B23;
  display: grid;
  place-content: center;

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
  border:1px solid #F6EAE5


}

.save-button:hover {
  background: #000000;
}
.drop-zone {
  padding:10px 0px
}
</style>
