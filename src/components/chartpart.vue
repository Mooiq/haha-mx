<template>
    <div class="chartbox">
        <div class="userinfo">
            <div class="userinfo-img">
                <a href="javascript:;">
                    <img :src="userIMG" height="200" width="200" alt="" />
                </a>
            </div>
            <div class="username">
                <a href="javascript:;">{{userID}}</a>
                <b></b>
                <p>{{releasetime}}</p>
            </div>
            <div class="readall">
                <a href="javascript:;">查看全文</a>
            </div>
        </div>
        <div class="usermsg">
            <p>{{somejock}}</p>
            <img  :class="{big: large}" :src="someIMG" @click="large = !large" />
        </div>
        <div class="userreply">
            <!-- 空 -->
        </div>
        <div class="userstar">
            <div class="goodorbad">
                <a class="good" @click.once="zan++" href="javascript:;">{{zan}}</a>
                <a class="bad" @click.once="pei++" href="javascript:;">{{pei}}</a>
            </div>
            <div class="share">
                <a href="javascript:;" @mouseover='seen = true' @mouseout='seen = false'>举报</a>|
                <a href="javascript:;">收藏</a>|
                <a href="javascript:;">分享</a>
                <a class="comment" href="javascript:;">评论({{report}})</a>
                <div class="report" v-show="seen" @mouseover="seen = true" @mouseout='seen = false'>
                    <ul>
                        <li><a href="javascript:;">广告</a></li>
                        <li><a href="javascript:;">看过100遍了</a></li>
                        <li><a href="javascript:;">内容不和谐</a></li>
                        <li><a href="javascript:;">其他原因</a></li>
                    </ul>
                </div>
            </div>
        </div>
    </div>
</template>

<script>


export default{
    name:'chartpart',
    props:['somejock','someIMG'],
    data () {
        return{
            userID:'Mofish摸鱼',
            userIMG: require('../assets/user/1.jpg'),
            // somejock: '本人9*年，男，想安稳了！现在想找个老实女孩子接盘，这几年经常混迹各种酒吧会所，有时也会嫖妓，做做推油。之前的女朋友大概有十五个左右，每个都嬲过，最多的一个嬲了一年半，后来因为自己太贪玩所以都没走下去，现在玩累了想安稳下来，特意想找个老实的女孩子在一起结婚生活，没啥特别的要求，只希望你能有房子有车子，身高170以上，体重100左右，胸部一定B以上，这辈子最讨厌胸部小的女人',
            // someIMG: require('../assets/user/a9d3fd1f4134970ab5d9159995cad1c8a6865dd9.jpg'),
            releasetime:'04-16 17:18',
            seen:false,
            large: false,
            zan: 0,
            pei: 0,
            report: 0
        }
    },
    methods:{
        
    },
    
}
</script>

<style scoped>
    .chartbox{
        width: 100%;
        padding: 20px;
        margin-top: 15px;
        margin-bottom: 15px;
        box-sizing: border-box;
        background: #fff;
    }
    .chartbox a{
        font-size: 12px;
        color: #b69e88;
    }
    .userinfo{
        width: 100%;
        height: 34px;
        display: flex;
        flex-direction: row;
    }
    .userinfo-img{
        width: 36px;
        height: 36px;
        margin-right: 10px;
    }
    .userinfo-img img{
        width: 100%;
        height: 100%;
    }
    .username{
        margin-right: auto;
    }
    .username p{
        margin: 0;
        margin-top: 3px;
        font-size: 12px;
        color: #999;
    }
    .usermsg{
        margin: 15px 0;
        width: 100%;
    }
    .usermsg img{
        width: auto;
        height: 60px;
        cursor: pointer;
    }
    .usermsg .big{
        max-width: 70%;
        height: auto;
    }
    .usermsg p{
        margin: 15px 0;
        font-size: 14px;
        line-height: 24px;
    }
    .userstar{
        width: 100%;
        height: 28px;
        font-size: 12px;
        color: #b69e88;
        display: flex;
        flex-direction: row;
    }
    .goodorbad{
        margin-right: auto;
    }
    .goodorbad a{
        display: inline-block;
        height: 28px;
        line-height: 28px;
        padding: 0 8px 0 32px;
        margin-right: 6px;
        border: 1px solid #e8e8e8;
        border-radius: 3px;
        background: url('../assets/icon-vote-new.png') no-repeat #fff;
    }
    a.good{
        background-position: 8px -128px;
        color: #66b946;
    }
    a.bad{
        background-position: 8px -26px;
        color: #fb5e4e;
    }
    .goodorbad a:hover{
        border-color: #bababa;
    }
    a.good:hover{
        background-position: 8px -129px;
    }
    a.bad:hover{
        background-position: 8px -25px;
    }
    .share{
        margin-top: 5px;
    }
    .share a{
        position: relative;
        display: inline-block;
        height: 22px;
        line-height: 22px;
        margin-right: 5px;
    }
    a.comment{
        padding: 0 8px 0 28px;
        border: 1px solid #e8e8e8;
        background: url('../assets/icon.png') 8px -182px no-repeat #fff;
        border-radius: 3px;
    }
    .comment:hover{
        border-color: #bababa;
    }
    .report{
        position: absolute;
        border: 1px solid #b69e88;
        width: 90px;
        background-color: #fff;
        z-index: 10;
        /*display: none;*/
    }
    .report ul{
        list-style: none;
    }
    .report li{
        height: 24px;
        line-height: 24px;
        padding: 0 8px;
    }
    .report li a{
        color: #999;
    }
    .report li:hover{
        background-color: #b69e88;
    }
    .report li:hover a{
        color: #fff;
    }
</style>