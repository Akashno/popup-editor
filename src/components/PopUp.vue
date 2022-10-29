<template>
  <div class="wrapper">
    <!-- Side Bar -->
    <SideBar @updateBgColor="updateBgColor" @updateStarColor="updateStarColor" />

    <!-- Canvas -->
    <div class="canvas">
      <div class="circle" ref="circle">
        <!-- Stars -->
        <div @mousedown="dragStars" class="stars" ref="draggableStar" id="draggable-star" @click="setCurrentItem('')">
          <Stars :starColor="starColor" />
        </div>
        <!-- Header -->
        <div @mousedown="dragHeader" ref="draggableHeader" id="draggable-header" @click="setCurrentItem('header')">
          <h1 :class="selectedObject === 'header' && 'selectedObject'" class="header " id="header" draggable="true"
            ref="header">
            All the text and elements in this popup should be editable and dragable
          </h1>
        </div>
        <!-- Input field -->
        <div @mousedown="dragInput" ref="draggableInput" id="draggable-input" @click="setCurrentItem('email-input')">
          <input ref="email-input" :class="selectedObject === 'email-input' && 'selectedObject'" id="email-input" class="email-input "
            type="text" placeholder="E-mail" draggable="true">
        </div>
        <div>
          <!-- Signup button -->
          <div class="" @mousedown="dragButton" ref="draggableButton" id="draggable-button"
            @click="setCurrentItem('signup-button')">
            <button :class="selectedObject === 'signup-button' && 'selectedObject'" ref="signup-button"
              class="signup-button " id="signup-button" @click="setCurrentItem('signup-button')">SIGNUP NOW</button>
          </div>
          <!-- subHeader -->
          <div class="drop-zone" ref="draggableSubHeader" id="draggable-subheader" @mousedown="dragSubHeader"
            @click="setCurrentItem('subHeader')">
            <span :class="selectedObject === 'subHeader' && 'selectedObject'" class="subHeader " ref="subHeader"
              id="subHeader" draggable="true">No credit card required. No surprises</span>
          </div>
        </div>

      </div>
    </div>
    <RightBar @setFont="setFont" :selectedObject="selectedObject" @setFontSize="setFontSize" />
    <!-- Save Buton -->
    <SaveButton @click="saveDesign()" />
  </div>
</template>


<!-- Add "scoped" attribute to limit CSS to this component only -->
<script>
import SideBar from './SideBar.vue'
import RightBar from './RightBar.vue'
import Stars from './Stars.vue'
import SaveButton from './SaveButton.vue'
export default {
  components: { RightBar, SideBar, Stars, SaveButton },
  data() {
    return {
      bgColor: "#DE795E",
      starColor: "#C85943",
      star: null,
      header: null,
      input: null,
      button: null,
      subHeader: null,
      selectedObject: ''
    }
  },
  mounted() {
    class Position {
      constructor() {
        this.clientX = undefined
        this.clientY = undefined
        this.movementX = 0
        this.movementY = 0
      }
      updateClientPos(clientX, clientY) {
        this.clientX = clientX
        this.clientY = clientY
      }
      updateMovement(movementX, movementY) {
        this.movementX = movementX
        this.movementY = movementY
      }
    }
    this.star = new Position()
    this.header = new Position()
    this.input = new Position()
    this.button = new Position()
    this.subHeader = new Position()
  },
  methods: {
    setFontSize(size) { this.$refs[this.selectedObject].style.fontSize = size + 'px' },
    setTextAlign(align) { this.$refs[this.selectedObject].style.textAlign = align },
    setCurrentItem(item) { this.selectedObject = item },
    setFont(font) { this.$refs[this.selectedObject].style.fontFamily = font },
    setPos(item, movementY, movementX) {
      this.$refs[item].style.top = (this.$refs[item].offsetTop - movementY) + 'px'
      this.$refs[item].style.left = (this.$refs[item].offsetLeft - movementX) + 'px'
    },
    dragStars: function (event) {
      event.preventDefault()
      this.star.updateClientPos(event.clientX, event.clientY)
      document.onmousemove = this.elementStarDrag
      document.onmouseup = this.closeDragElement
    },
    elementStarDrag: function (event) {
      event.preventDefault()
      this.star.updateMovement(this.star.clientX - event.clientX, this.star.clientY - event.clientY)
      this.star.updateClientPos(event.clientX, event.clientY)
      this.setPos('draggableStar', this.star.movementY, this.star.movementX)
    },
    dragHeader: function (event) {
      event.preventDefault()
      this.header.updateClientPos(event.clientX, event.clientY)
      document.onmousemove = this.elementHeaderDrag
      document.onmouseup = this.closeDragElement
    },
    elementHeaderDrag: function (event) {
      event.preventDefault()
      this.header.updateMovement(this.header.clientX - event.clientX, this.header.clientY - event.clientY)
      this.header.updateClientPos(event.clientX, event.clientY)
      this.setPos('draggableHeader', this.header.movementY, this.header.movementX)
    },

    dragInput: function (event) {
      event.preventDefault()
      this.input.updateClientPos(event.clientX, event.clientY)
      document.onmousemove = this.elementInputDrag
      document.onmouseup = this.closeDragElement
    },
    elementInputDrag: function (event) {
      event.preventDefault()
      this.input.updateMovement(this.input.clientX - event.clientX, this.input.clientY - event.clientY)
      this.input.updateClientPos(event.clientX, event.clientY)
      this.setPos('draggableInput', this.input.movementY, this.input.movementX)
    },
    dragButton: function (event) {
      event.preventDefault()
      this.button.updateClientPos(event.clientX, event.clientY)
      document.onmousemove = this.elementButtonDrag
      document.onmouseup = this.closeDragElement
    },
    elementButtonDrag: function (event) {
      event.preventDefault()
      this.button.updateMovement(this.button.clientX - event.clientX, this.button.clientY - event.clientY)
      this.button.updateClientPos(event.clientX, event.clientY)
      this.setPos('draggableButton', this.button.movementY, this.button.movementX)
    },

    dragSubHeader: function (event) {
      event.preventDefault()
      this.subHeader.updateClientPos(event.clientX, event.clientY)
      document.onmousemove = this.elementSubHeaderDrag
      document.onmouseup = this.closeDragElement
    },
    elementSubHeaderDrag: function (event) {
      event.preventDefault()
      this.subHeader.updateMovement(this.subHeader.clientX - event.clientX, this.subHeader.clientY - event.clientY)
      this.subHeader.updateClientPos(event.clientX, event.clientY)
      this.setPos('draggableSubHeader', this.subHeader.movementY, this.subHeader.movementX)
    },

    closeDragElement() {
      document.onmouseup = null
      document.onmousemove = null
    },
    saveDesign() {
      console.log('saved design')
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

.signup-button:hover,
.email-input:hover,
.header:hover,
.subHeader:hover,
.stars:hover {

  outline: 2px dashed #201c1c;
  border: 2px dashed #201c1c;
  border-radius: 10px;
  cursor: move
}

.selectedObject {
  outline: 2px dashed #201c1c;
  border: 2px dashed #201c1c;
  border-radius: 10px;
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


.draggable-header {
  resize: both;
}

.header {
  max-width: 25rem;
  display: flex;
  resize: both;
  align-items: center;
  justify-content: center;
  color: #FEFEFD;
  margin: auto;
  font-weight: 900;
}

.subHeader {
  color: #F6EAE5;
  padding: 5px;
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
  position: relative;

}

.canvas {
  width: 100vw;
  height: 100vh;
  background: #1A1B23;
  display: grid;
  place-content: center;

}

/* initial positions of draggable elements */
#draggable-star,
#draggable-header,
#draggable-input,
#draggable-button,
#draggable-subheader {
  position: absolute;
  z-index: 9;
  width: 90%
}

#draggable-star {
  top: 10%;
  left: 50%;
  transform: translate(-50%, -50%);
}

#draggable-header {
  top: 32%;
  left: 50%;
  transform: translate(-50%, -50%);
}

#draggable-input {
  top: 55%;
  left: 50%;
  transform: translate(-50%, -50%);
}

#draggable-button {
  top: 70%;
  left: 50%;
  transform: translate(-50%, -50%);
}

#draggable-subheader {
  bottom: 10%;
  left: 50%;
  transform: translate(-50%, -50%);
}

.stars {
  width: 100px;
}
</style>
