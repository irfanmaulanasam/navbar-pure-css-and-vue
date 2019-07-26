<template>    
    <div class="tree-menu">
        <div class="label-wrapper" @click="toggleChildren">
            <div :style="indent" :class="labelClasses">
                <slot v-if="nodes">&#9663;</slot>
                <a href="#">{{ label }}</a>
            </div>
        </div>
        <section v-if="showChildren">
            <tree-menu 
            v-for="node in nodes" 
            :nodes="node.children" 
            :label="node.label"
            :depth="depth + 1"   
            :key="node.id"
            >
        </tree-menu>
        </section>
    </div>
</template>

<script>
export default {
    name: 'tree-menu',
  props: [ 'nodes', 'label', 'depth' ],
  data() {
     return {
       showChildren: false
     }
  },
  computed: {
    iconClasses() {
      return {
        'fa-plus-square-o': !this.showChildren,
        'fa-minus-square-o': this.showChildren
      }
    },
    labelClasses() {
      return { 'has-children': this.nodes }
    },
    indent() {
      return { transform: `translate(${this.depth * 20}px)` }
    }
  },
  methods: {
    toggleChildren() {
       this.showChildren = !this.showChildren;
    }
  }
}
</script>