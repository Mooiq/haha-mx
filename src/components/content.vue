<template>
<div class="contentwrap">
   <div class="contentpage">
    <Contentleft></Contentleft>
    <Carousel></Carousel>
    <Contentright></Contentright>
  </div> 
</div>
  
</template>

<script>
import Carousel from './carousel'
import Contentleft from './contentleft'
import Contentright from './contentright'

export default {
  name: 'contentpage',
  components:{
    Carousel,
    Contentleft,
    Contentright
  },
  data () {
    return {
       
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.contentwrap{
    background: #f9f2e2;
}
.contentpage{
    width: 1080px;
    margin: 0 auto;
    display: flex;
    flex-direction: row;
    background: #f1e7ce;
  }
</style>