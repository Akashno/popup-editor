<template>
<div class="side-bar">
      <p class="title">Customize</p>
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
<div class="editor-input-item">
        <p>
          <label for="favcolor" class="editor-item-label">Header Text</label>
        </p>
          <textarea  v-model="header" @input="setHeader" class="header-input"  />
      </div>
<div class="editor-input-item">
        <p>
          <label for="favcolor" class="editor-item-label">Button Text</label>
        </p>
          <textarea  v-model="button" @input="setButtonText" class="button-input"  />
      </div>
<div class="editor-input-item">
        <p>
          <label for="favcolor" class="editor-item-label">Sub header text</label>
        </p>
          <textarea  v-model="subHeader" @input="setSubHeader" class="subheader-input"  />
      </div>
      </div>

    </div>
</template>

<script>

export default {
    props:{
        selectedObject:{
            type:String
        }
    },
    data(){
        return{
            bgColor:"#DE795E",
            starColor:"#C85943",
            header:"All the text and elements in this popup should be editable and dragable",
            button:"SIGNUP NOW",
            subHeader:'No credit card required. No surprises',
        }
    },
    methods:{
        setHeader(){ 
            document.getElementById('header').innerHTML = this.header },
        setButtonText(){ document.getElementById('signup-button').innerHTML = this.button },
        setSubHeader(){ document.getElementById('subHeader').innerHTML = this.subHeader }
    }
}
</script>

<style scoped>
.editor-item-label{
  font-size: 10px;
}
.editor-item{
  display:flex;
  align-items: center;
  flex-wrap: wrap;
}
textarea{
    max-width:200px;
    height:100px;
  background:#1A1B23;
    padding:10px;
    color: #F6EAE5;

}
.editor-item span{
  width: 80px;
}
.title{
  font-size: 15px;
}
.color-picker{
  background:"#1E1E21"

}
.side-bar {
  text-align: left;
  padding:20px 20px ;
  color:#F6EAE5;
  width: 15vw;
  background:#27272F;
  border-top-right-radius: 10px;
  border-bottom-right-radius: 10px;

}

</style>