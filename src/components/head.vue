<template>
  <div class="headpage">
    <div class="header-top">
      <h4>
        <a href="https://www.haha.mx">
          <img src="../assets/logo_v3.png" height="60" width="180" alt="" />
        </a>
      </h4>
  
      <ul class="title-ul">
        <!-- 点击一条高亮显示：每次点击都会通过Inactive函数的参数(title)获取到当前点击标签的title，把这个title值赋给activeTitle，所以每次点击的那个标签的title一定等于activeTitle，从而获取active效果；而每次点的标签不同一定会使activeTitle值变化导致跟上次点击的title值不同，所以上一个标签就会丢失active效果 -->
        <li v-for="title in titles" :class="{active: title.name == activeTitle}" @click="Inactive(title.name)">
          <router-link to="/">{{title.name}}</router-link>
        </li>
      </ul>

      <router-link to="" class="talk">讲一个</router-link>

      <form action="" method="post" name="search">
        <div class="header-top-search">
          <div @mouseover="seen = true" @mouseout="seen = false">
            <span class="search-joke" :class="{arrow_up:seen}">{{Osearchtitle}}</span>
            <ul class="search-down-ul" v-if="seen">
              <li v-for="searchTitle in searchTitles" @click="searcChange(searchTitle)">{{searchTitle.name}}</li>
            </ul>
          </div>
          <input type="text" placeholder="搜索你感兴趣的笑话" :placeholder="placeholders"/>
          <button type="submit"></button>
        </div>
      </form>

    </div>
  </div>
</template>

<script>
export default {
  name: 'headpart',
  data () {
    return {
      titles:[
              {name:'首页',href:''},
              {name:'新哈哈',href:''},
              {name:'热门评论',href:''},
              {name:'搞笑图片',href:''},
              {name:'热门话题',href:''},
              {name:'美女直播',href:''}
            ],
      activeTitle: '首页',
      seen: false,
      searchTitles: [
                    {name:'搜笑话',plc:'搜索你感兴趣的笑话'},
                    {name:'搜话题',plc:'搜索你感兴趣的话题'}
                    ],
      Osearchtitle: '搜笑话',
      placeholders: '搜索你感兴趣的笑话'
    }
  },
  methods:{
    Inactive: function(name){
      // alert(title);
      this.activeTitle = name
    },
    searcChange: function(searchTitle){
      this.Osearchtitle = searchTitle.name;
      this.placeholders = searchTitle.plc;
      this.seen = false;
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
  a{
    text-decoration: none;
    color: #2c3e50;
    cursor: pointer;
  }
  ul{
    list-style: none;
  }
  ul.title-ul a:hover{
    color:#fd7647;
  }
  .headpage{
    border-bottom: 2px solid #ddd;
  }
  .header-top{
    width: 1080px;
    height: 58px;
    padding: 13px 0;
    margin: 0 auto;
    font-size: 16px;
    display: flex;
    flex-direction: row;
    align-items: center;
  }
  h4{
    margin: 0;
    margin-right: 8px;
  }
  ul.title-ul{
    display: flex;
    flex-direction: row;
    align-items: center;
  }
  ul.title-ul li{
    height: 30px;
    line-height: 30px;
    border-radius: 3px;
    padding: 0 14px;
    margin-right: 5px;
  }
  .active{
    background: #f8f2e2;
  }
  .talk{
    font-size: 14px;
    font-weight: 700;
    width: 90px;
    height: 35px;
    line-height: 35px;
    margin-left: 15px;
    margin-right: auto;
    background: #fd7647;
    color: #fff;
    border-radius: 3px;
    text-align: center;
  }
  .talk:hover{
    background: rgb(251,139,85);
  }
  .header-top-search{
    width: 212px;
    height: 24px;
    border: 1px solid #e6e6e6;
    border-top-width: 2px;
    background: #fafafa;
    display: flex;
    flex-direction: row;
    justify-content: space-between;
  }
  .search-joke{
    display: block;
    width: 56px;
    font-size: 12px;
    padding-left: 6px;
    line-height: 24px;
    background: url('../assets/arrow_down.png') 50px center no-repeat;
    cursor: pointer;
  }
  .arrow_up{
    background: url('../assets/arrow_up.png') 50px center no-repeat;
  }
  .search-down-ul{
    width: 62px;
    font-size: 12px;
    box-shadow: 1px 1px 1px #aaa;
  }
  .search-down-ul li{
    width: 100%;
    height: 24px;
    line-height: 24px;
    text-align: center;
    cursor: pointer;
  }
  .search-down-ul li:hover{
    background: #f1752a;
    color: #fff;
  }
  .header-top-search input{
    outline: 0;
    border: none;
    background: #fafafa;
    color: #b7b7b7;
    width: 110px;
    height: 18px;
    margin: 3px 0 0;
    font-size: 12px;
    border-right: 1px solid #ebebeb;
    border-left: 1px solid #ebebeb;
    padding-left: 6px;
    flex-grow: 1;
  }
  .header-top-search button{
    outline: 0;
    border: 0;
    width: 26px;
    height: 24px;
    cursor: pointer;
    background: url('../assets/icon.png') 5px -83px no-repeat #fafafa;
  }
</style>