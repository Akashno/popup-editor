<template>
  <div class="wrapper">
    <!-- Side Bar -->
    <SideBar @updateBgColor="updateBgColor" @updateStarColor="updateStarColor" />
    <!-- Canvas -->
    <div class="canvas">
      <div class="circle" ref="circle">
        <!-- Stars -->
        <div @mousedown="dragStars" class="stars" ref="draggableStar" id="draggable-star">
          <Stars :starColor="starColor" />
        </div>
        <!-- Header -->
        <div @mousedown="dragHeader" ref="draggableHeader" id="draggable-header">
          <h1 class="header " id="header" draggable="true" ref="header">
            All the text and elements in this popup should be editable and dragable
          </h1>
        </div>
        <!-- Input field -->
        <div @mousedown="dragInput" ref="draggableInput" id="draggable-input">
          <input id="email-input" class="email-input " type="text" placeholder="E-mail" draggable="true">
        </div>
        <div>

        <!-- Signup button -->
        <div class="" @mousedown="dragButton" ref="draggableButton" id="draggable-button">
          <button class="signup-button " id="signup-button">SIGNUP NOW</button>
        </div>

        <!-- subHeader -->
        <div class="drop-zone" ref="draggableSubHeader" id="draggable-subheader" @mousedown="dragSubHeader">
          <span class="subHeader " id="subHeader" draggable="true">No credit card required.
            No surprises</span>
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
  components: { SideBar, Stars, SaveButton },
  data() {
    return {
      bgColor: "#DE795E",
      starColor: "#C85943",
      star: null,
      header: null,
      input: null,
      button: null,
      subHeader: null,
    }
  },
  mounted() {
    class Position {
      constructor(cx, cy, mx, my) {
        this.clientX = cx
        this.clientY = cy
        this.movementX = mx
        this.movementY = my
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
    this.star = new Position(undefined, undefined, 0, 0)
    this.header = new Position(undefined, undefined, 0, 0)
    this.input = new Position(undefined, undefined, 0, 0)
    this.button = new Position(undefined, undefined, 0, 0)
    this.subHeader = new Position(undefined, undefined, 0, 0)
  },
  methods: {
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
.stars-container:hover {
  outline: 2px solid #201c1c;
  border: 2px solid #201c1c;
  border-radius: 10px;
  cursor:move

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
  padding:5px;
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

.reset-button {
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
  right: 200px;
  border-radius: 10px;
  box-shadow: 20px 20px 50px rgb(53, 49, 49);
  border: 1px solid #F6EAE5
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
</style>
