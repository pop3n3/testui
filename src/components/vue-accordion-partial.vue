<template>
<li :style="[liStyles,wdStyle]" v-on:mouseover="mouseOver($event)">
</li>
</template>
<script>
export default {
  props: {
    item: {
      type: Object
    },
    styles: {
      type: Object
    }
  },
  data () {
    return {
      wdStyle: {
        // width: 100 + '%'
      }
    }
  },
  methods: {
    mouseOver: function (event) {
      var clientWidth = document.documentElement.clientWidth
      if (clientWidth < 1000) {
        clientWidth = 1000
      }
      var per = clientWidth / 7.0
      var currentWidth = this.item.width
      var x = (clientWidth - currentWidth) / 6.0
      var otherRs = x / per * 100 + '%'
      var rs = currentWidth / per * 100 + '%'
      // this.wdStyle = {
      //   width: rs
      // }
      console.log('clientWidth:' + clientWidth + ' ,otherRs:' + otherRs + ', rs:' + rs)
    }
  },
  computed: {
    liStyles () {
      const li = {
        backgroundImage: 'url(' + this.item.image + ')'
      }
      if (this.styles && this.styles.li) {
        Object.assign(li, this.styles.li)
      }
      return li
    }
  }
}
</script>
<style>
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
.vue-accordion ul:hover li { width: 57.7%; }
.vue-accordion ul:hover li:hover { width: 353.74%; }
</style>
