<template>
  <div class="carouselOut">
    <div class="carouselcontent">
      <div class="carouselBox" @mouseover="clearTimer" @mouseout="play">
        <transition-group :name="slide" tag='ul' class="wrap-ul">
            <li v-for="(wrap ,index) in wraps" :key="index" v-if="action == index">
              <a :href="wrap.to">
                <img :src="wrap.src" :alt="wrap.alt" :title="wrap.alt"/>
              </a>
            </li>
        </transition-group>
        <ul class="paging-ul">
          <li v-for="(pag ,index) in wraps" :class="{active: action == index}" :key="index" @click="activing(index)"></li>
        </ul>
        <div class="lastPic" @click="last"></div>
        <div class="nextPic" @click="next"></div>
      </div>
      <div class="carouselDown">
        <h3>话题推荐</h3>
        <ul class="carouselDown-ul">
          <li v-for="title in titles">
            <a href="#">
              {{title.name}}
            </a>
          </li>
        </ul>
        <a class="more" href="#">更多 ></a>
      </div>
    </div>
    <ul>
      <li :is="'Chartpart'" v-for="msg in msgs" :somejock="msg.Msg" :someIMG="msg.Src"></li>
    </ul>

    <Talksome v-on:bus="addinfo"></Talksome>
  </div>
</template>

<script>

import MsgBus from '@/components/msgbus.js'
import Chartpart from './chartpart'
import Talksome from './talksome'

export default {
  name: 'carousel',
  components:{
    Chartpart,
    Talksome
  },
  data () {
    return {
      test:'',
      action: '0',
      timer: null,
      slide: 'slideL',
      wraps:[
            // 图片地址直接写加载不出来，必须这样写才可以src:require('URL')
            {name:'1',src:require('../assets/broadcast/1651.jpg'),alt:'举报',to:"#"},
            {name:'2',src:require('../assets/broadcast/1652.jpg'),alt:'哈哈',to:"#"},
            {name:'3',src:require('../assets/broadcast/1653.jpg'),alt:'挖矿',to:"#"},
            {name:'4',src:require('../assets/broadcast/1654.jpg'),alt:'社区',to:"#"}
          ],
      titles:[
            {name:'小编招募',to:"#"},
            {name:'每日烧脑',to:"#"},
            {name:'小编说',to:"#"},
            {name:'瞎ＪＢ说',to:"#"}
          ],
      msgs:[
            {Msg:'同事兴高采烈的说 “前女友生的孩子特别像我” 对面女同事淡定地来了句 “她嫁了你妈的前男友”',Src:require('../assets/user/badad933c895d143ce72575478f082025aaf073a.jpg')},
            {Msg:'电影《比得兔》是一部由英国百年经典IP改编的真人动画电影，影片讲述了田园冒险大王“比得兔”（詹姆斯·柯登 James Corden 配音）带领一众伙伴，与麦格雷戈（多姆纳尔·格里森 Domhnall Gleeson 饰）叔侄二人，为争夺菜园主权和隔壁美丽女主人贝伊（萝丝·拜恩 Rose Byrne 饰）的喜爱而斗智斗勇、各显神通的爆笑故事。随着人兔大战不断升级，一系列欢乐闹趣、令人捧腹、啼笑皆非的趣事也由此引发。',Src:require('../assets/user/ui3WO.jpg')},
            {Msg:'本人9*年，男，想安稳了！现在想找个老实女孩子接盘，这几年经常混迹各种酒吧会所，有时也会嫖妓，做做推油。之前的女朋友大概有十五个左右，每个都嬲过，最多的一个嬲了一年半，后来因为自己太贪玩所以都没走下去，现在玩累了想安稳下来，特意想找个老实的女孩子在一起结婚生活，没啥特别的要求，只希望你能有房子有车子，身高170以上，体重100左右，胸部一定B以上，这辈子最讨厌胸部小的女人',Src:require('../assets/user/a9d3fd1f4134970ab5d9159995cad1c8a6865dd9.jpg')}
        ]
    }
  },
  methods:{
    activing: function(index){
      if (index < this.action) {
        //如果点击按钮index小于当前action值，就把<transition>的name绑定另一个class值，也是实现了换向滑动
        this.slide = 'slideR'
      }
      this.action = index
    },
    Autoplay: function(){
      this.action++;
      if (this.action >= this.wraps.length) {
        this.action = 0
      }
    },
    play: function(){
      this.timer = setInterval(this.Autoplay, 2500)
    },
    clearTimer: function(){
      clearInterval(this.timer)
    },
    last: function(){
      this.slide = 'slideR';
      this.action--;
      if (this.action < 0) {
        this.action = this.wraps.length-1;
      }
    },
    next: function(){
      this.action++;
      if (this.action >= this.wraps.length) {
        this.action = 0
      }
    },
    addinfo: function(info){
        this.msgs.unshift({
          'Msg': info.Msg,
          'Src': info.Src
      });
        console.log(this.msgs)
    }
  },
  created: function(){
    this.play();
  },
  updated: function(){
    this.slide = 'slideL'
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
  ul{
      list-style: none;
    }

  .carouselOut{
    width: 600px;
    margin-top: 15px;
    background: #f1e7ce;
  }
  .carouselcontent{
    height: 195px;
  }

  .carouselDown{
    width: 100%;
    box-sizing: border-box;
    background: #fff;
  }
  .carouselBox{
    width: 100%;
    height: 150px;
    overflow: hidden;
    position: relative;
  }
  .wrap-ul{
    width: 100%;
    height: 150px;
    display: flex;
    flex-direction: row;
    position: relative;
  }
  .wrap-ul li{
    position: absolute;     /*这一步很重要，不然动画进入和划出只能显示其中一种！！！*/
  }
  .paging-ul{
    width: 32px;
    height: 12px;
    padding: 0 15px;
    border-radius: 6px;
    background: #333;
    opacity: 0.8;
    display: flex;
    flex-direction: row;
    justify-content: center;
    align-items: center;
    /*transform: translate(300px, -16px); *//*本行和下面三行效果对等*/
    position: relative;
    left: 295px;
    top: -16px;
  }
  .active{
    background: #666!important;
  }
  .lastPic{
    width: 20px;
    height: 30px;
    background: url('../assets/arrow.png') no-repeat;
    position: absolute;
    top: 60px;
    cursor: pointer;
  }
  .nextPic{
    width: 20px;
    height: 30px;
    background: url('../assets/arrow.png') -30px 0 no-repeat;
    position: absolute;
    right: 0;
    top: 60px;
    cursor: pointer;
  }
  .paging-ul li{
    width: 6px;
    height: 6px;
    border-radius: 3px;
    background: #fff;
    margin-left: 2px;
    cursor: pointer;
  }
  .slideL-enter-active {  
    transform: translateX(0);  
    transition: all 1.5s ease;  
  }  
  .slideL-leave-active {  
    transform: translateX(-100%);  
    transition: all 1.5s ease;  
  }  
  .slideL-enter {  
    transform: translateX(100%);  
  }  
  .slideL-leave {  
    transform: translateX(0);  
  } 

  .slideR-enter-active {  
    transform: translateX(0);  
    transition: all 1.5s ease;  
  }  
  .slideR-leave-active {  
    transform: translateX(100%);  
    transition: all 1.5s ease;  
  }  
  .slideR-enter {  
    transform: translateX(-100%);  
  }  
  .slideR-leave {  
    transform: translateX(0);  
  }




  .carouselDown{
    width: 100%;
    height: 44px;
    box-sizing: border-box;
    padding: 8px 10px;
    font-size: 12px;
    color: #333;
    display: flex;
    flex-direction: row;
  }
  .carouselDown h3{
    width: 48px;
    height: 28px;
    margin: 0;
    padding-right: 10px;
    line-height: 28px;
    color: #666;
    font-size: 100%;
    font-weight: 400;
    cursor: text;
  }
  .carouselDown ul{
    width: 480px;
    height: 28px;
    display: flex;
    flex-direction: row;
    justify-content: flex-start;
    align-items: center;
  }
  .carouselDown ul li{
    width: 48px;
    height: 24px;
    line-height: 24px;
    padding-left: 15px;
    padding-right: 20px;
    margin-right: 6px;
    border-radius: 15px;
    background: url('../assets/icon.png') right -1174px no-repeat #f6f6f6;
  }
  .carouselDown ul li:hover{
    background: url('../assets/icon.png') right -1174px no-repeat #f1e7ce;
  }
  .carouselDown ul li a{
    color: #b69e88;
  }
  .more{
    display: block;
    width: 37px;
    height: 28px;
    line-height: 28px;
    color: #b69e88;
  }
</style>