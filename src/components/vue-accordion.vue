<template>
<div :class="accordionClass" :style="divStyles">
<ul v-on:mouseleave="mouseOut()">
<li v-for="(item,index) in items" v-on:mouseover="mouseOver(index)" :id="index" :item="item" :key="index" :style="{backgroundImage: 'url(' + item.image + ')'}">
</li>
</ul>
</div>
</template>
<script>
// <partial-accordion v-for="(item,index) in items" :item="item" :key="index" :styles="styles"></partial-accordion>
// import partialAccordion from './vue-accordion-partial.vue'
export default {
  name: 'vue-accordion',
  props: {
    items: {
      type: Array
    },
    styles: {
      type: Object,
      default: function () {
        return {}
      }
    },
    accordionClass: {
      type: String,
      default: 'vue-accordion'
    }
  },
  methods: {
    mouseOver: function (index) {
      var clientWidth = document.documentElement.clientWidth
      if (clientWidth < 1000) {
        clientWidth = 1000
      }
      let count = 7.0
      var per = clientWidth / count
      var currentWidth = this.items[index].width
      var x = (clientWidth - currentWidth) / (count - 1.0)
      var otherRs = x / per * 100 + '%'
      var rs = currentWidth / per * 100 + '%'
      for (var i = 0; i < count; i++) {
        var obj = document.getElementById(i)
        if (i === index) {
          obj.style.width = rs
        } else {
          obj.style.width = otherRs
        }
      }
    },
    mouseOut: function () {
      let count = 7.0
      var clientWidth = document.documentElement.clientWidth
      if (clientWidth < 1000) {
        clientWidth = 1000
      }
      var per = clientWidth / count * 100 + '%'
      for (var i = 0; i < count; i++) {
        var obj = document.getElementById(i)
        obj.style.width = per
      }
    }
  },
  computed: {
    divStyles () {
      return this.styles && this.styles.div ? this.styles.div : {}
    }
  }
}
</script>
<style>
.vue-accordion {
width: 100%;
overflow: hidden;
height: 600px;
min-width: 1200px;
}
.vue-accordion ul {
width: 100%;
height: 100%;
display: table;
table-layout: fixed;
margin: 0;
padding: 0;
}
.vue-accordion ul li {
display: table-cell;
vertical-align: bottom;
position: relative;
width: 100%;
background-repeat: no-repeat;
background-position: center center;
transition: all 500ms ease;
height: 100%;
}
/* .vue-accordion ul:hover li { width: 57.7%; } */
/* .vue-accordion ul:hover li:hover { width: 353.74%; } */
</style>
