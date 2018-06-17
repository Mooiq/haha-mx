<template>
  <div class="contentright">
    <ul class="adv-ul">
        <li v-for="adv in advs">
            <a :href="adv.to">
                <img :src="adv.src" alt="" title="adv.title"/>
            </a>
        </li>
    </ul>
  </div>
</template>

<script>
export default {
  name: 'contentright',
  data () {
    return {
      advs:[
            {title:'哈哈安卓客户端',src:require('../assets/rightAds/weixin-v8.jpg'),to:'#'},
            {title:'',src:require('../assets/rightAds/0f000cHteSXqHfFNEiNzQ0.jpg'),to:'https://www.baidu.com'}
      ]
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
    .contentright{
        width: 300px;
        margin-top: 15px;
        margin-left: 15px;
    }
    .adv-ul{
        list-style: none;
    }
    .adv-ul li{
        margin-bottom: 15px;
    }
</style>