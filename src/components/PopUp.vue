<template>
  <div class="wrapper">
<div class="side-bar">
        <button class="save-button">Save Design</button>
      <p class="customize">Customize</p>
      <hr>
      <div class="editor-items">

      <div class="editor-item">
        <span>
          <label for="favcolor" class="editor-item-label">Background</label>
        </span>
          <input  v-model="bgColor" class="color-picker" type="color" id="favcolor" name="favcolor" value="#ff0000" @input="changeBackgroundColor()"><br><br>
      </div>
      </div>

    </div>
    <div class="canvas">
    <div class="circle" ref="circle">
      <div>
        <div  class="stars" ref="star" >
          <svg  class="star" fill="#C85943" width="40" height="40" viewBox="0 0 24 24"
            xmlns="http://www.w3.org/2000/svg">
            <path
              d="M12.5 17.925 6.629 21l1.121-6.512L3 9.875l6.564-.95L12.5 3l2.936 5.925 6.564.95-4.75 4.613L18.371 21z" />
          </svg>
          <svg class="star" fill="#C85943" width="50" height="50" viewBox="0 0 24 24"
            xmlns="http://www.w3.org/2000/svg">
            <path
              d="M12.5 17.925 6.629 21l1.121-6.512L3 9.875l6.564-.95L12.5 3l2.936 5.925 6.564.95-4.75 4.613L18.371 21z" />
          </svg>
          <svg class="star" fill="#C85943" width="40" height="40" viewBox="0 0 24 24"
            xmlns="http://www.w3.org/2000/svg">
            <path
              d="M12.5 17.925 6.629 21l1.121-6.512L3 9.875l6.564-.95L12.5 3l2.936 5.925 6.564.95-4.75 4.613L18.371 21z" />
          </svg>
        </div>
        <h1 class="header" draggable="true" contenteditable="true" ondragover="allowDrop(event)">
          All the text and elements in this popup should be editable and dragable
        </h1>
        <div>
          <input class="email-input"  type="text"  placeholder="E-mail" draggable="true">
        </div>
        <div>
          <button class="signup-button" draggable="true" contenteditable="true">SIGNUP NOW</button>
          <p class="subHeader" contenteditable="true">No credit card required. No surprises</p>
        </div>
      </div>
    </div>
    </div>
    
  </div>
</template>


<!-- Add "scoped" attribute to limit CSS to this component only -->
<script>
export default {
  data(){
    return {
      bgColor:"#DE795E",
      positions: {
        clientX: undefined,
        clientY: undefined,
        movementX: 0,
        movementY: 0
      }
    }

  },
  methods:{
    changeBackgroundColor(){
      this.$refs.circle.style.background=this.bgColor
      this.$refs.circle.style.boxShadow = `0 0 0 8px ${this.bgColor}`
    },
      dragMouseDown: function (event) {
      event.preventDefault()
      // get the mouse cursor position at startup:
      this.positions.clientX = event.clientX
      this.positions.clientY = event.clientY
      document.onmousemove = this.elementDrag
      document.onmouseup = this.closeDragElement
    },
    elementDrag: function (event) {
      event.preventDefault()
      this.positions.movementX = this.positions.clientX - event.clientX
      this.positions.movementY = this.positions.clientY - event.clientY
      this.positions.clientX = event.clientX
      this.positions.clientY = event.clientY
      // set the element's new position:
      this.$refs.star.style.top = (this.$refs.star.offsetTop - this.positions.movementY) + 'px'
      this.$refs.star.style.left = (this.$refs.star.offsetLeft - this.positions.movementX) + 'px'
    },
    closeDragElement () {
      document.onmouseup = null
      document.onmousemove = null
    }
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
.save-button{
  position:absolute;
  bottom:10px;
  width:100px;
  left:20px;
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



.wrapper{
  display: flex;
}
.canvas{
  width:100vw;
  height: 100vh;
  background: #2c2c2c;
  display: grid;
  place-content: center;
  
}
.side-bar {
  height:80vh; 
  margin-top:auto ;
  margin-bottom: auto;
  margin-left: 10px;
  text-align: left;
  padding: 0px 10px;
  border-right: solid  #757575;
  color:#F6EAE5;
  width: 15vw;
  background:#2c2c2c;
  position:relative;
  box-shadow:  0 0 2px 2px #494A4E;
  border-radius: 10px;

}
.editor-item-label{
  font-size: 10px;
}


.editor-item{
  display:flex;
  align-items: center;
  gap:10px;
}
.customize{
  font-size: 15px;
}
.color-picker{
  background:"#1E1E21"

}

</style>
