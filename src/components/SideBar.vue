<template>
<div class="side-bar">
      <p class="customize">Customize</p>
      <hr>
      <div class="editor-items">

      <div class="editor-item">
        <span>
          <label for="favcolor" class="editor-item-label">Background</label>
        </span>
          <input  v-model="bgColor" class="color-picker" type="color" id="favcolor" name="favcolor" value="#ff0000" @input="$emit('updateBgColor',bgColor)"><br><br>
      </div>
       <div class="editor-item">
        <span>
          <label for="favcolor" class="editor-item-label">Star color</label>
        </span>
          <input  v-model="starColor" class="color-picker" type="color" id="favcolor" name="favcolor" value="#ff0000" @input="$emit('updateStarColor',starColor)"><br><br>
      </div>
      </div>

    </div>
</template>

<script>
export default {

    data(){
        return{
      bgColor:"#DE795E",
      starColor:"#C85943",
        }
    }
}
</script>

<style>
.editor-item-label{
  font-size: 10px;
}

.editor-item{
  display:flex;
  align-items: center;
  gap:20px;
}
.editor-item span{
  width: 80px;
}
.customize{
  font-size: 15px;
}
.color-picker{
  background:"#1E1E21"

}
.side-bar {
  height:80vh; 
  margin-top:auto ;
  margin-bottom: auto;
  margin-left: 10px;
  text-align: center;
  border-right: solid  #757575;
  color:#F6EAE5;
  width: 15vw;
  background:#2c2c2c;
  box-shadow:  0 0 2px 2px #242121;
  border-radius: 10px;

}

</style>