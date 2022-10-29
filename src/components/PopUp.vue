<template>
  <div class="wrapper">


    <!-- Side Bar -->

    <SideBar @updateBgColor="updateBgColor" @updateStarColor="updateStarColor"  />
    <!-- Canvas -->
    <div class="canvas" @dragover="drag_over($event)" @drop="drop($event)">
      <div class="circle" ref="circle">
        <div @mousedown="dragStars" class="stars"   ref="draggableContainer" id="draggable-container">
             <Stars :starColor="starColor" id="drag1" /> 
          </div>
          <div  @mousedown="dragHeader" ref="draggableHeaderContainer" id="draggable-header-container">
            <h1 class="header " id="header"  draggable="true" ref="header">
              All the text and elements in this popup should be editable and dragable
            </h1>
          </div>
          <div  @mousedown="dragInput" ref="draggableInputContainer" id="draggable-input-container">
            <input  id="email-input" class="email-input " type="text" placeholder="E-mail" draggable="true">
          </div>
          <div>
            <div class="" @mousedown="dragButton" ref="draggableButtonContainer" id="draggable-button-container">
              <button class="signup-button "  id="signup-button" >SIGNUP NOW</button>
            </div>
            <div class="drop-zone" ref="draggableSubHeaderContainer" id="draggable-subheader-container" @mousedown="dragSubHeader">
              <p class="subHeader "  id="subHeader" draggable="true">No credit card required.
                No surprises</p>
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
      star:null,
      header:null,
      input:null,
      button:null,
      subHeader:null,
    }
  },
  mounted(){
    class Position{
      constructor(){
          this.clientX =  undefined,
          this.clientY =  undefined,
          this.movementX =  0,
          this.movementY = 0
      }
      
      updateClientX(clientX){
        this.clientX = clientX
      }
      updateClientY(clientY){
        this.clientY = clientY
      }
      updateMovementX(movementX){
        this.movementX = movementX
      }
      updateMovementY(movementY){
        this.movementY = movementY
      }
    }
      this.star = new Position()
        this.header =new Position()
        this.input = new Position()
        this.button = new Position()
        this.subHeader = new Position()
  },
  methods: {
     dragStars: function (event) {
      event.preventDefault()
      this.star.updateClientX(event.clientX)
      this.star.updateClientY(event.clientY)
      document.onmousemove = this.elementStarDrag
      document.onmouseup = this.closeDragElement
    },
    elementStarDrag: function (event) {
      event.preventDefault()
      this.star.updateMovementX(this.star.clientX - event.clientX)
      this.star.updateMovementY(this.star.clientY - event.clientY)
      this.star.updateClientX(event.clientX)
      this.star.updateClientY(event.clientY)
      this.$refs.draggableContainer.style.top = (this.$refs.draggableContainer.offsetTop - this.star.movementY) + 'px'
      this.$refs.draggableContainer.style.left = (this.$refs.draggableContainer.offsetLeft - this.star.movementX) + 'px'
    },

     dragHeader: function (event) {
      event.preventDefault()
      this.header.updateClientX(event.clientX)
      this.header.updateClientY(event.clientY)
      document.onmousemove = this.elementHeaderDrag
      document.onmouseup = this.closeDragElement
    },
    elementHeaderDrag: function (event) {
      event.preventDefault()
      this.header.updateMovementX(this.header.clientX - event.clientX)
      this.header.updateMovementY(this.header.clientY - event.clientY)
      this.header.updateClientX(event.clientX)
      this.header.updateClientY(event.clientY)
      this.$refs.draggableHeaderContainer.style.top = (this.$refs.draggableHeaderContainer.offsetTop - this.header.movementY) + 'px'
      this.$refs.draggableHeaderContainer.style.left = (this.$refs.draggableHeaderContainer.offsetLeft - this.header.movementX) + 'px'
    },

     dragInput: function (event) {
      event.preventDefault()
      this.input.updateClientX(event.clientX)
      this.input.updateClientY(event.clientY)
      document.onmousemove = this.elementInputDrag
      document.onmouseup = this.closeDragElement
    },
    elementInputDrag: function (event) {
      event.preventDefault()
      this.input.updateMovementX(this.input.clientX - event.clientX)
      this.input.updateMovementY(this.input.clientY - event.clientY)
      this.input.updateClientX(event.clientX)
      this.input.updateClientY(event.clientY)
      this.$refs.draggableInputContainer.style.top = (this.$refs.draggableInputContainer.offsetTop - this.input.movementY) + 'px'
      this.$refs.draggableInputContainer.style.left = (this.$refs.draggableInputContainer.offsetLeft - this.input.movementX) + 'px'
    },
     dragButton: function (event) {
      event.preventDefault()
      this.button.updateClientX(event.clientX)
      this.button.updateClientY(event.clientY)
      document.onmousemove = this.elementButtonDrag
      document.onmouseup = this.closeDragElement
    },
    elementButtonDrag: function (event) {
      event.preventDefault()
      this.button.updateMovementX(this.button.clientX - event.clientX)
      this.button.updateMovementY(this.button.clientY - event.clientY)
      this.button.updateClientX(event.clientX)
      this.button.updateClientY(event.clientY)
      this.$refs.draggableButtonContainer.style.top = (this.$refs.draggableButtonContainer.offsetTop - this.button.movementY) + 'px'
      this.$refs.draggableButtonContainer.style.left = (this.$refs.draggableButtonContainer.offsetLeft - this.button.movementX) + 'px'
    },

     dragSubHeader: function (event) {
      event.preventDefault()
      this.subHeader.updateClientX(event.clientX)
      this.subHeader.updateClientY(event.clientY)
      document.onmousemove = this.elementSubHeaderDrag
      document.onmouseup = this.closeDragElement
    },
    elementSubHeaderDrag: function (event) {
      event.preventDefault()
      this.subHeader.updateMovementX(this.subHeader.clientX - event.clientX)
      this.subHeader.updateMovementY(this.subHeader.clientY - event.clientY)
      this.subHeader.updateClientX(event.clientX)
      this.subHeader.updateClientY(event.clientY)
      this.$refs.draggableSubHeaderContainer.style.top = (this.$refs.draggableSubHeaderContainer.offsetTop - this.subHeader.movementY) + 'px'
      this.$refs.draggableSubHeaderContainer.style.left = (this.$refs.draggableSubHeaderContainer.offsetLeft - this.subHeader.movementX) + 'px'
    },
    closeDragElement () {
      document.onmouseup = null
      document.onmousemove = null
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
#draggable-container, #draggable-header-container,#draggable-input-container,#draggable-button-container,#draggable-subheader-container {
  position: absolute;
  z-index: 9;
  width:90%

}

#draggable-container{
  top:10%;
  left: 50%;
  transform: translate(-50%, -50%);
}
#draggable-header-container{
  top:32%;
  left: 50%;
  transform: translate(-50%, -50%);
}

#draggable-input-container{
  top:55%;
  left: 50%;
  transform: translate(-50%, -50%);
}

#draggable-button-container{
  top:70%;
  left: 50%;
  transform: translate(-50%, -50%);
}
#draggable-subheader-container{
  bottom:5%;
  left: 50%;
  transform: translate(-50%, -50%);
}
</style>
