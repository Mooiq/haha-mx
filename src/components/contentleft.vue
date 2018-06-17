<template>
  <div class="contentleft" @mouseout="hiddenlist">
    <ul class="left-ul">
        <li v-for="title in leftnavlist" @mouseover="showlist(title)">
            <img :src="title.src" alt=""/>
            <a href="#">{{title.name}}</a>
        </li>
    </ul>
    <div class="left-ul-list" v-if="seen" @mouseover="seen = true" @mouseout="seen = false">
        <ul class="left-ul-list-ul">
            <li v-for="listname in list">
                <a :href="listname.to">{{listname.name}}</a>
            </li>
        </ul>
    </div>
  </div>
</template>

<script>
export default {
  name: 'contentleft',
  data () {
    return {
      leftnavlist:[
            {name:'哈哈MX',src:require('../assets/leftnav/leftnav_0.png'),to:"#",
             list:[ {name:'上升快',to:'#'},
                    {name:'蘑菇推荐',to:'#'},
                    {name:'7天哈哈',to:'#'},
                    {name:'30天哈哈',to:'#'},
                    {name:'年度哈哈',to:'#'},
                    {name:'小编说',to:'#'},
                    {name:'瞎ＪＢ说',to:'#'},
                    {name:'蘑菇广播',to:'#'},
                    {name:'一日一囧',to:'#'},
                    {name:'每日萌宠',to:'#'}
                  ]
            },
            {name:'爆笑段子',src:require('../assets/leftnav/leftnav_1.png'),to:"#",
             list:[ {name:'幽默笑话',to:'#'},
                    {name:'搞笑段子',to:'#'},
                    {name:'内涵段子',to:'#'},
                    {name:'经典笑话',to:'#'},
                    {name:'国际笑话',to:'#'},
                    {name:'古今笑话',to:'#'},
                    {name:'校园笑话',to:'#'},
                    {name:'糗人糗事',to:'#'},
                    {name:'冷笑话',to:'#'},
                    {name:'老笑话',to:'#'}
                  ]
            },
            {name:'搞笑图片',src:require('../assets/leftnav/leftnav_10.png'),to:"#",
             list:[ {name:'趣图',to:'#'},
                    {name:'内涵图片',to:'#'},
                    {name:'恶搞图片',to:'#'},
                    {name:'表情包',to:'#'},
                    {name:'gif动态图',to:'#'},
                    {name:'聊天图片',to:'#'},
                    {name:'ps图片搞笑',to:'#'},
                    {name:'搞笑照片',to:'#'},
                    {name:'微信搞笑图片',to:'#'},
                    {name:'看图说话',to:'#'}
                  ]
            },
            {name:'美女福利',src:require('../assets/leftnav/leftnav_2.png'),to:"#",
             list:[ {name:'美女搞笑',to:'#'},
                    {name:'恶搞美女',to:'#'},
                    {name:'美女直播',to:'#'},
                    {name:'深夜福利',to:'#'},
                    {name:'车展美女',to:'#'},
                    {name:'美腿福利',to:'#'},
                    {name:'女汉子',to:'#'},
                    {name:'女神',to:'#'},
                    {name:'萌妹子',to:'#'},
                    {name:'女司机',to:'#'}
                  ]
            },
            {name:'爆笑童语',src:require('../assets/leftnav/leftnav_3.png'),to:"#",
             list:[ {name:'熊孩子',to:'#'},
                    {name:'童年趣事',to:'#'},
                    {name:'童年无忌',to:'#'},
                    {name:'儿童笑话',to:'#'},
                    {name:'毁童年',to:'#'},
                    {name:'小学生',to:'#'},
                    {name:'逆天小孩',to:'#'},
                    {name:'童话',to:'#'},
                    {name:'萌宝',to:'#'},
                    {name:'小明系列',to:'#'}
                  ]
            },
            {name:'搞笑动物',src:require('../assets/leftnav/leftnav_4.png'),to:"#",
             list:[ {name:'搞笑动物图片',to:'#'},
                    {name:'搞笑宠物',to:'#'},
                    {name:'萌物',to:'#'},
                    {name:'狗狗搞笑图片',to:'#'},
                    {name:'猫猫搞笑图片',to:'#'},
                    {name:'大熊猫搞笑图片',to:'#'},
                    {name:'羊驼搞笑图片',to:'#'},
                    {name:'经典动物笑话',to:'#'},
                    {name:'猪猪搞笑图片',to:'#'},
                    {name:'大猩猩搞笑图片',to:'#'}
                  ]
            },
            {name:'GET正能量',src:require('../assets/leftnav/leftnav_5.png'),to:"#",
             list:[ {name:'一句话经典语录',to:'#'},
                    {name:'励志语录',to:'#'},
                    {name:'名人名言',to:'#'},
                    {name:'心灵鸡汤',to:'#'},
                    {name:'深度好文',to:'#'},
                    {name:'幽默语录',to:'#'},
                    {name:'情感语录',to:'#'},
                    {name:'爱情语句',to:'#'},
                    {name:'褝训',to:'#'},
                    {name:'箴言',to:'#'}
                  ]
            },
            {name:'漫画大全',src:require('../assets/leftnav/leftnav_6.png'),to:"#",
             list:[ {name:'搞笑漫画',to:'#'},
                    {name:'幽默漫画',to:'#'},
                    {name:'内涵漫画',to:'#'},
                    {name:'恶搞漫画',to:'#'},
                    {name:'恐怖漫画',to:'#'},
                    {name:'邪恶漫画',to:'#'},
                    {name:'原创漫画',to:'#'},
                    {name:'暴走漫画',to:'#'},
                    {name:'妈妈再打我一次',to:'#'},
                    {name:'邪恶小漫画',to:'#'}
                  ]
            },
            {name:'两性幽默',src:require('../assets/leftnav/leftnav_7.png'),to:"#",
             list:[ {name:'夫妻笑话',to:'#'},
                    {name:'情侣笑话',to:'#'},
                    {name:'成人笑话',to:'#'},
                    {name:'污段子',to:'#'},
                    {name:'荤段子',to:'#'},
                    {name:'家有悍妻',to:'#'},
                    {name:'二货老婆',to:'#'},
                    {name:'绿帽子',to:'#'},
                    {name:'隔壁老王',to:'#'},
                    {name:'啪啪啪',to:'#'}
                  ]
            },
            {name:'节日笑话',src:require('../assets/leftnav/leftnav_8.png'),to:"#",
             list:[ {name:'情人节',to:'#'},
                    {name:'愚人节',to:'#'},
                    {name:'儿童节',to:'#'},
                    {name:'教师节',to:'#'},
                    {name:'七夕节',to:'#'},
                    {name:'中秋节',to:'#'},
                    {name:'双十一',to:'#'},
                    {name:'感恩节',to:'#'},
                    {name:'圣诞节',to:'#'},
                    {name:'除夕',to:'#'}
                  ]
            },
            {name:'求助专区',src:require('../assets/leftnav/leftnav_9.png'),to:"#",
             list:[ {name:'求车牌',to:'#'},
                    {name:'求番号',to:'#'},
                    {name:'求片名',to:'#'},
                    {name:'求大神',to:'#'},
                    {name:'求科普',to:'#'},
                    {name:'求游戏',to:'#'},
                    {name:'求真相',to:'#'},
                    {name:'求安慰',to:'#'},
                    {name:'求解答',to:'#'},
                    {name:'小调查',to:'#'}
                  ]
            },
            {name:'所有话题',src:require('../assets/leftnav/syht.png'),to:"#"}
      ],
      list:[],
      seen: false
    }
  },
  methods:{
    showlist: function(title){
        this.list = title.list;
        if (title.name != '所有话题') {
           this.seen = true; 
        };
    },
    hiddenlist: function(){
        this.seen = false;
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
    .contentleft{
        margin-top: 15px;
        position: relative;
    }
    ul{
        list-style: none;
    }
    .left-ul{
        width: 150px;
        height: 447px;
        text-align: left;
    }
    .left-ul li{
        height: 36px;
        line-height: 36px;
    }
    .left-ul li img{
        padding-left: 16px;
        margin-right: 10px;
        vertical-align: middle;
    }
    .left-ul li a{
        font-size: 14px;
    }
    .left-ul li:hover{
        background: #fa5f37;
    }
    .left-ul li:hover a{
        color: #fff;
    }

    .left-ul-list{
        width: 140px;
        height: 390px;
        position: absolute;
        top: 0;
        left: 100%;
        z-index: 1;
        background: #fff;
    }
    .left-ul-list-ul li{
        height: 36px;
        line-height: 36px;
        padding-left: 16px;
        margin-bottom: 3px; 
    }
    .left-ul-list-ul li a{
        font-size: 14px;
        color: #a78d74;
    }
    .left-ul-list-ul li:hover{
        background: #f9f2e3;
    }
    .left-ul-list-ul li:hover a{
        color: #fa5f38;
    }
</style>