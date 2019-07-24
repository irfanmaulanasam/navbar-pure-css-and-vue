<template>
    <div id="navbar">
        <div class="container">
            <section class="parent" v-for="item in menu" :key="item.id">
                <div class="parent-link">
                {{item.label}}
                </div>
                <treeMenu
                :nodes="item.children"
                :depth="0"
                />
            </section>
        </div>
    </div>
</template>
<script>
import datamenu from './assets/menu'
import treeMenu from './components/treemenunavbar'
export default {
    name:'navbar',
    components:{
        treeMenu
    },
    data(){
        return {
            menu:datamenu.children
        }
    },
}
</script>
<style>
.container{
    display:flex;
    direction: column;
}
.parent{
    background-color: brown;
    color: antiquewhite;
    margin-inline-start: 1em;
    padding: 5px;
    outline: 1px dashed black;
}
</style>
