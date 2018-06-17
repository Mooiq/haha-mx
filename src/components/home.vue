<template>
  <div class="homepage">
    <headpart></headpart>
    <contentpart></contentpart>
    <footpart></footpart>
  </div>
</template>

<script>

import headpart from './head'
import contentpart from './content'
import footpart from './foot'

export default {
  name: 'homepage',
  components:{
    headpart,
    contentpart,
    footpart
  },
  data () {
    return {
      
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

</style>