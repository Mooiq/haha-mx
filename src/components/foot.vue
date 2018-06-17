<template>
  <div class="footpage">
    <div class="foot-adv">
        <div class="adv">
            <a href="#">
                <img src="../assets/rightAds/0f000j1FY_bkyl3FJ2tGa6.jpg" height="90" width="960" alt="" />
            </a>
        </div> 
    </div>

    <div class="foot-hold">
        <div class="haha">
            <p>精彩哈哈</p>
            <ul>
                <li><a href="#">热门哈哈</a></li>
                <li><a href="#">热门标签</a></li>
                <li><a href="#">哈哈MX趣图</a></li>
                <li><a href="#">关于哈哈</a></li>
                <li><a href="#">免责声明</a></li>
                <li><a href="#">意见反馈</a></li>
            </ul>
        </div>

        <div class="haha">
            <p>加入&合作</p>
            <ul>
                <li>哈哈用户QQ群：98540200</li>
                <li>哈哈小编招募群：204735383</li>
                <li></li>
                <li>违法及不良信息举报电话：</li>
                <li>010-80699110</li>
                <li>举报邮箱：</li>
                <li>jubao@maxthon.net</li>
                <li>商务合作：</li>
                <li>hz@maxthon.net</li>
            </ul>
        </div>

        <div class="haha">
            <p>关注哈哈</p>
            <ul>
                <li>微信关注</li>
                <img src="../assets/weixin/haha_weixin.jpg" height="112" width="112" alt="" />
                <li>下载app</li>
                <img src="../assets/weixin/haha_down.png" height="112" width="112" alt="" />
            </ul>
        </div>

        <div class="haha">
            <p>友情连接</p>
            <div class="friendlinkbox">
                <ul class="friendlink">
                    <li><a href="#">遨游浏览器</a></li>
                    <li><a href="#">遨游今日</a></li>
                    <li><a href="#">爱看新闻</a></li>
                    <li><a href="#">爱奇艺搞笑视频</a></li>
                    <li><a href="#">考拉FM电台</a></li>
                    <li><a href="#">hao123网址导航</a></li>
                    <li><a href="#">2345网址导航</a></li>
                    <li><a href="#">1616网址导航</a></li>
                    <li><a href="#">哈哈MX趣图</a></li>
                </ul>
                <ul class="friendlink">
                    <li><a href="#">企业秀</a></li>
                    <li><a href="#">安全联盟</a></li>
                </ul>
            </div>
            
        </div>
    </div>
  </div>
</template>

<script>
export default {
  name: '',
  data () {
    return {
      
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
    .footpage{
        width: 100%;
        height: 480px;
        padding-top: 20px;
        padding-bottom: 20px;
        color: #7b7b7b;
    }
    .foot-adv{
        width: 960px;
        margin: 0 auto;
    }
    .foot-hold{
        width: 1080px;
        margin: 0 auto;
        padding: 14px;
        display: flex;
        flex-direction: row;
    }
    .haha{
        width: 270px;
    }
    .haha p{
        display: block;
        color: #333;
        padding: 0 0 10px;
        margin: 0;
        font-weight: 700;
        font-size: 18px;
    }
    .haha ul{
        list-style: none;
    }
    .haha ul li{
        width: auto;
        height: 28px;
        line-height: 28px;
        font-size: 12px;
        color: #333;
    }
    .haha ul li a{
        font-size: 12px;
    }
    .haha ul img{
        margin-bottom: 10px;
    }
    .friendlinkbox{
        display: flex;
        flex-direction: row;
    }
    .friendlink{
        width: 120px;
    }
</style>