<template>
<div class="right-bar" >
      <p class="title">Text Style</p>
      <div class="editor-items">
      <div class="editor-item">
        <p>
          <label for="font" class="editor-item-label">Font</label>
        </p>
        <select :disabled="!selectedObject" name="font" v-model="selectedFont" id="font"  @change="setFont()">
          <option :value="font" v-for="font in fontFamily">{{font}}</option>
        </select>
      </div>
      <div class="editor-item">
        <p>
          <label for="font" class="editor-item-label">Size</label>
        </p>
        <input :disabled="!selectedObject" class="font-input" type="number" v-model="fontSize" @input="setFontSize()">
      </div>
      </div>

    </div>
</template>

<script>

export default {
  props:{
    selectedObject: {
      type: String
    }
  },
    data(){
        return{
            fontSize:28,
            fontFamily:[
              "'Times New Roman', Times, serif",
              "Arial, Helvetica, sans-serif",
              "'Lucida Console', 'Courier New', monospace"
            ],
            selectedFont:"'Times New Roman', Times, serif",

        }
    },
    methods:{
        setHeader(){ document.getElementById('header').innerHTML = this.header },
        setButtonText(){ document.getElementById('signup-button').innerHTML = this.button },
        setSubHeader(){ document.getElementById('subHeader').innerHTML = this.subHeader },
        setFont(){ this.$emit('setFont',this.selectedFont) },
        setFontSize(){ this.$emit('setFontSize',this.fontSize) }
    }
}
</script>

<style scoped>
select:focus{
  border:none;
  outline:none;
}
select{
  background:#1A1B23;
  width:100%;
  color:#F6EAE5;
  border: none;
  padding:10px 2px;
}
.font-input{
  width:40px;
  background:#1A1B23;
  padding:10px 5px;
  color:white;
  border:none;
}
.editor-item-label{
  font-size: 10px;
}
.editor-item{
  margin-bottom:10px;

}
textarea{
    max-width:200px;
    height:100px;
    background: #27272F;
    padding:10px;
    color: #F6EAE5;

}
.editor-item span{
  width: 80px;
}
.title{
  font-size: 15px;
}
.right-bar {
  margin-bottom: auto;
  text-align: left;
  padding:20px 20px ;
  color:#F6EAE5;
  width: 15vw;
  background:#27272F;
  border-top-right-radius: 10px;
  border-bottom-right-radius: 10px;

}

</style>