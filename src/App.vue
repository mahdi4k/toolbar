<template>
  <div id="app">
    <div class="row">
      <div >
        <ToolbarItems @shortkeySelected="shortkeySelected" @customChange="selectedToolbar" />
      </div>
      <div class="col-main">
        Chosen tool : {{toolbarName}} Mode
      </div>
      <div class="guide-box">
         <span>ESC ShortKey: <span class="font-weight">switch to hand mode</span></span>
         <span>A ShortKey: <span class="font-weight">switch to Window mode</span></span>
         <span>S ShortKey: <span class="font-weight">switch to Pencil mode</span></span>
         <span>D ShortKey: <span class="font-weight">switch to MagicPen mode</span></span>
         <span>F ShortKey: <span class="font-weight">switch to Brush mode</span></span>
         <span>E ShortKey: <span class="font-weight">switch to Eraser mode</span></span>
         <span>W ShortKey: <span class="font-weight">switch to Location mode</span></span>
         <span>Q ShortKey: <span class="font-weight">switch to Crosshairs mode</span></span>
      </div>
    </div>
  </div>
</template>

<script>
import ToolbarItems from './components/ToolbarItems.vue'

export default {
  name: 'App',
  components: {
    ToolbarItems
  },
  data(){
    return{
      toolbarName : 'Select'
    }
  },
  methods:{
    selectedToolbar(val){
      this.toolbarName = val
    },
    shortkeySelected(val){
      this.toolbarName = val
    }
  }
}
</script>

<style>
@import "assets/style.css";
body{
  margin: 0;
}
.row{
  display: flex;
  position: relative;
}
.col-main{
  margin-left: 5rem;
  margin-top: 2rem;
  font-size: 15pt;
}
.font-weight{
  font-weight: bold;
}
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

.guide-box{
  display: flex;
  flex-direction: column;
  justify-content: flex-end;
  margin-right: 60px;
  place-items: baseline;
  position: absolute;
  right: 0;
  bottom: 19px;
  background-color: #ccc;
  padding: 24px;
  border-radius: 13px;
}
.guide-box span{
  margin-bottom: 8px;
}

</style>
