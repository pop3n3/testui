<template>
<div>
  <div class="d1">
  </div>
  <vue-accordion :items="items">
  </vue-accordion>
</div>
</template>

<script>
import vueAccordion from './vue-accordion.vue'
export default {
  name: 'HelloWorld',
  components: {
    vueAccordion
  },
  data () {
    return {
      items: [
        {image: '/static/1.png', width: 897},
        {image: '/static/2.jpg', width: 450},
        {image: '/static/3.jpg', width: 800},
        {image: '/static/4.jpg', width: 800},
        {image: '/static/5.jpg', width: 800},
        {image: '/static/6.jpg', width: 800},
        {image: '/static/7.jpg', width: 874}
      ]
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.d1{
  width: 100%;
  height: 400px;
  background-color: orangered;
}
/* .vue-accordion ul:hover li { width: 2%; } */
</style>
