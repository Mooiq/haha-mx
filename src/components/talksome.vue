<template>
    <div >
        <div class="talkwrap">
            <div class="talkbox">
                <div class="statement">
                    <h2>发帖须知：</h2>
                    <div>
                        <span>严禁发布：</span>
                        <p>政治、色情、广告、诽谤、歧视等内容。</p>
                    </div>
                    <div>
                        <span>信息审核：</span>
                        <p>您提交的内容经过审核后才能发布，提交上述违规内容不予通过。情节严重者封停并永久清除账号信息。</p>
                    </div>
                </div>
                <div class="talkform">
                    <h2>分享一切好笑的事情：</h2>
                    <span class="donot">请勿发布违禁内容，否则一律封禁</span>
                    <div class="jokeinput">
                        <textarea name="jokeshare" class="jokeshare" placeholder="分享你的笑话" v-model="msg" value="msg"></textarea>
                    </div>
                    <div class="emoji">
                        <div class="getpic">
                            <div :class="[{icon: isicon},{point: ispoint}]">
                                <img src="../assets/camera.png" height="20" width="20" alt="" />
                                <span>图片</span>
                            </div>
                            <input name="files" type="file" class="input-file" accept="image/*" @change="getPic" @mouseover="isicon=!isicon,ispoint=!ispoint" @mouseout="isicon=!isicon,ispoint=!ispoint"/>
                        </div>
                        <button class="release" @click="sendMsg">发布</button>
                    </div>
                    <div class="showpic" v-show="seepic" >
                        <span class="removepic" @click="cancelpic"></span>
                        <img :src="src" height="auto" width="160" alt=""/>
                    </div>
                </div>
            </div>
        </div>
    </div>
</template>

<script>

import MsgBus from '@/components/msgbus.js'

export default{
    name: 'talksome',
    components:{
        
    },
    data () {
        return{
            msg:'',
            src:'',
            load: require('../assets/loading.gif'),
            isicon: true,
            ispoint: false,
            seepic: false,
            info:{Msg:'',Src:''}
        }
    },
    methods:{
        getPic: function () {
                //在涉及到使用window对象的函数的时候最好把this提前赋给一个变量，这样可以避免出错
                var vm = this;
                    vm.seepic = true;
                    vm.src = vm.load;
                var reader = new FileReader();
                var file = document.querySelector('.input-file').files[0];
                reader.readAsDataURL(file);
                reader.onloadend = function (event) {
                    vm.src = reader.result;
                    // console.log(vm.src);
                }     
            },
        cancelpic: function(){
            this.seepic = false;
            this.src = '';
        },
        sendMsg: function(){
            if (this.msg != '' || this.src != '') {
                this.info.Msg = this.msg;
                this.info.Src = this.src;
                this.$emit('bus',this.info);
                // console.log(this.info);
                this.msg = '';
                this.src = '';
            }else{
                alert('请分享你的趣事^.^!')
            };
        }
    }
}
</script>

<style scoped>
    input{
        outline: 0;
        background: 0 0;
        border: none;
    }
    .talkwrap{
        overflow: hidden;
        background-color: #f1e7ce;
    }
    .talkbox{
        width: 600px;
        margin: 0 auto;
        margin-top: 16px;
        font-size: 12px;
        color: #333;
    }
    .statement{
        width: 100%;
        height: 148px;
        box-sizing: border-box;
        padding: 16px;
        background: #fff;
        border-radius: 6px;
        margin-bottom: 16px;
    }
    .statement span{
        display: inline-block;
        float: left;
        color: #b99e87;
    }
    .statement p{
        display: block;
        margin-left: 70px;
    }
    .talkbox h2{
        display: inline-block;
        width: 300px;
        font-size: 15px;
        font-weight: 400;;
        margin: 0;
        padding: 0;
        margin-bottom: 6px;
    }
    .talkform{
        width: 100%;
        box-sizing: border-box;
        border-radius: 6px;
        padding: 16px;
        background: #fff;
        margin-bottom: 100px;
    }
    span.donot{
        display: inline-block;
        width: 180px;
        height: 24px;
        line-height: 24px;
        color: #fd7647;
        float: right;
    }
    .jokeshare{
        outline: 0;
        resize:none ;
        width: 100%;
        border: 1px solid #e1ded9;
        border-radius: 2px;
        padding: 5px;
        height: 100px;
        box-sizing: border-box;
        margin-top: 10px;
        font-family: monospace;
    }
    .emoji{
        width: 100%;
        height: 26px;
        margin: 10px 0;
    }
    .getpic{
        width: 70px;
        height: 25px;
        display: inline-block;
        position: relative;
    }
    .getpic input{
        width: 100%;
        height: 100%;
        font-size: 0;
        opacity: 0;
        cursor: pointer;
    }
    .getpic span{
        display: inline-block;
        float: right;
        padding-top: 2px;
    }
    .icon{
        width: 100%;
        height: 100%;
        box-sizing: border-box;
        padding: 3px 10px;
        position: absolute;
        top: 0;
        left: 0;
        background-color: #fff;
        border-radius: 3px;
    }
    .point{
        width: 100%;
        height: 100%;
        box-sizing: border-box;
        padding: 3px 10px;
        position: absolute;
        top: 0;
        left: 0;
        background-color: #f9f2e1;
        color: #b79e87;
        border-radius: 3px;
    }
    .release{
        outline: none;
        display: inline-block;
        width: 66px;
        height: 30px;
        line-height: 25px;
        text-align: center;
        font-size: 14px;
        background: #fd7647;
        border: 1px solid #ec5621;
        color: #fff;
        border-radius: 3px;
        float: right;
        cursor: pointer;
    }
    .release:hover{
        background: #fb8b55;
        border: 1px solid #f1752a;
    }
    .showpic{
        width: 160px;
        position: relative;
        overflow: hidden;
    }
    .removepic{
        display: block;
        width: 16px;
        height: 16px;
        position: absolute;
        top: 0;
        right: -16px;
        background: url('../assets/icon.png') left -846px no-repeat #fd9035;
        cursor: pointer;
    }
    .showpic:hover span{
        right: 0;
    }
</style>