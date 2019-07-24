<template>
    <div id="sidebar">
        <div class="container">
            <h4>testing recursive button<br/><small>(Recursive Components)</small></h4>
            <div id="app">
                <treeMenu 
                :nodes="daftarmenu.children" 
                :depth="0"   
                :label="daftarmenu.label"
                />
            </div>
        </div>
    </div>
</template>

<script>
import daftarmenu from './assets/menu'
import treeMenu from './components/treemenusidebar'
export default {
  name:'sidebar',
  data(){
      return {
          daftarmenu
      }
  },
  components:{
      treeMenu,
  }
}
</script>

<style>
body {
    /* background-color: cyan; */
    font-family: "Open Sans", sans-serif;
    font-size: 18px;
    font-weight: 300;
    line-height: 1em;
}
#app{
    background-color: brown;
    color: #ccc;
}
.sidebar{
    background-color: rgb(72, 72, 72);
}
.container {
    outline: 3px dashed blue;
    width: 300px;
    margin: 0 auto;
}

.tree-menu .label-wrapper {
    padding-bottom: 10px;
    margin-bottom: 10px;
    border-bottom: 1px solid #ccc;
}
.tree-menu .label-wrapper .has-children {
    cursor: pointer;
}

</style>

