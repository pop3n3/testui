<template>
<div class="vue-accordion">
<ul v-on:mouseleave="mouseLeave">
<li v-for="(item,index) in items" v-on:mouseenter="mouseOver(index)" :id="index" :item="item" :key="index" :style="{backgroundImage: 'url(' + item.image + ')'}">
</li>
</ul>
</div>
</template>
<script>
export default {
  name: 'vue-accordion',
  props: {
    items: {
      type: Array
    },
    lastTimer: null
  },
  methods: {
    mouseOver: function (index) {
      var clientWidth = document.documentElement.clientWidth
      if (clientWidth < 1000) {
        clientWidth = 1000.0
      }
      let count = this.items.length
      var per = clientWidth / count
      var currentWidth = this.items[index].width
      var x = (clientWidth - currentWidth) / (count - 1.0)
      var otherRs = x / per * 100.0 + '%'
      var rs = currentWidth / per * 100.0 + '%'
      var current = document.getElementById(index)
      current.style.width = rs
      for (var i = 0; i < count; i++) {
        var obj = document.getElementById(i)
        if (i !== index) {
          obj.style.width = otherRs
        }
      }
    },
    mouseLeave: function () {
      for (var i = 0; i < this.items.length; i++) {
        var obj = document.getElementById(i)
        obj.style.width = 100 + '%'
      }
    }
  }
}
</script>
<style>
.vue-accordion {
width: 100%;
overflow: hidden;
height: 600px;
min-width: 1000px;
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
height: 100%;
transition: all 0.5s ease;
-o-transition: all 0.5s ease; /* opera */
-ms-transition: all 0.5s ease; /* IE 10 */
-moz-transition: all 0.5s ease; /* Firefox */
-webkit-transition: all 0.5s ease; /*safari and chrome */
}
</style>
