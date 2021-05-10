<template>
  <div id="app">
    <div class="content">
      <div class="sideber">
        <ul>
          <li id="mineHeadImg"><img src="./assets/img/headImg/headImg2.jpg"></li>
          <li><img src="./assets/img/icon/消息(1).png"></li>
          <li><img src="./assets/img/icon/联系人.png"></li>
          <li><img src="./assets/img/icon/立方体.png"></li>
          <li id="more"><img src="./assets/img/icon/更多.png"></li>
        </ul>
      </div>
      <div class="userlist">
        <div class="search">
          <div class="searchinput">
            <div class="searchIcon">
            <img src="./assets/img/icon/搜索.png">
          </div>
          <input type="text" placeholder="搜索">
          <div class="addbtn">+</div>
          </div>
        </div>
        <!-- userlist组件部分 -->
        <userlist-com :userlist="userlist" @chooseuser="changeuser"></userlist-com>
      </div>
      <!-- 聊天部分 -->
      <div id="wechatLogo" v-if="!currentname">
        <img src="./assets/img/icon/微信.png">
      </div>
      <div class="chatwindow" v-if="currentname">
        <div class="topitem">
          <div class="currentname">
            {{ currentname }}
          </div>
          <ul class="toollist">
            <li><img src="./assets/img/icon/图钉.png"></li>
            <li><img src="./assets/img/icon/最小化.png"></li>
            <li><img src="./assets/img/icon/最大化.png"></li>
            <li><img src="./assets/img/icon/关闭.png"></li>
            <li id="toolmore"><img src=".\assets\img\icon\更多 (2).png" alt=""></li>
          </ul>
        </div>
        <div class="chatroom">
          <chatroom-com></chatroom-com>
        </div>

      </div>
    </div>
  </div>
</template>

<script>
 import userlistCom from './components/userlistCom.vue'
 import chatroomCom from './components/chatroomCom.vue'

export default {
  name: 'App',
  components: {
    userlistCom,chatroomCom
  },
  data() {
    return {
      currentname:false,
      userlist:[{
        username:"郭灿榕",
        headImg:require("./assets/img/headImg/headImg1.jpg")
      },{
        username:"倪成凯",
        headImg:require("./assets/img/headImg/headImg2.jpg")
      },{
        username:"陈剑峰",
        headImg:require("./assets/img/headImg/headImg4.jpg")
      },{
        username:"顾晨",
        headImg:require("./assets/img/headImg/headImg5.jpg")
      },{
        username:"柳源",
        headImg:require("./assets/img/headImg/headImg6.jpg")
      },],
    }
  },
  methods: {
    changeuser:function(item){
      //console.log(item);
      this.currentname = item.username
    }
  },
}
</script>

<style>
  ul,li{
    margin: 0;
    padding: 0;
    list-style: none;
  }
  input{
    border: 0px;
    outline: 0px;
  }
</style>

<style scoped>
  #wechatLogo{
    width: 100px;
    height: 100px;
    margin: 235px auto;
  }
  #wechatLogo img{
    width: 100px;
    height: 100px;
  }
  .content{
    margin: 50px auto;
    box-shadow: 0px 0px 20px rgb(182, 182, 182);
    width: 845px;
    height: 570px;
    display: flex;
    background-color: #f5f5f5;
  }
/* 第一部分 */
  .sideber{
    width: 55px;
    height: 570px;
    background-color: #282b2f;
  }
  .sideber ul{
    position: relative;
    width: 35px;
    height: 570px;
    margin: 0 auto;
  }
  .sideber img{
    padding: 5px 2.5px;
    width: 30px;
    height: 30px;
  }
  #mineHeadImg img{
    width: 35px;
    height: 35px;
    border-radius: 2px;
    padding: 20px 0;
  }
  #more{
    position: absolute;
    bottom: 8px;
  }
  #more img{
    padding-left: 5px;
    width: 25px;
    height: 25px;
  }
  /* 第二部分 */
  .userlist{
    -webkit-user-select:none;
    -moz-user-select:none;
    -ms-user-select:none;
    user-select:none;
    width: 250px;
    height: 570px;
    background-color: #ece9e8;
  }
  .userlist .search{
    width: 250px;
    /* height: 70px; */
    
  }
  .searchinput{
    margin: 25px auto;
    display: flex;
    width: 225px;
    height: 25px;
  }
  .searchIcon{
    width: 20px;
    height: 25px;
    padding-right: 5px;
    border-radius: 4px 0 0 4px;
    background-color: #dad9d8;
  }
  .searchIcon img{
    padding-left: 4px;
    padding-top: 4px;
    width: 17px;
  }
  .userlist .search input{
    padding: 0;
    width: 165px;
    height: 25px;
    border-radius: 0 4px 4px 0;
    background-color: #dad9d8;
  }
  .userlist .searchinput .addbtn{
    margin-left: 10px;
    color: #8b8b8b;
    width: 25px;
    height: 25px;
    text-align: center;
    line-height: 22px;
    border-radius: 4px;
    background-color: #dad9d8;
  }
  /* 第三部分 */
  .chatwindow{
    position: relative;
    width: 540px;
    height: 570px;
    background-color: #f5f5f5;
  }
  .chatwindow .topitem {
    -webkit-user-select:none;
    -moz-user-select:none;
    -ms-user-select:none;
    user-select:none;
    width: 100%;
    height: 60px;
    border-bottom: 1px solid #e7e7e7;
  }
  .chatwindow .topitem .currentname{
    padding-top: 3px;
    font-size: 20px;
    line-height: 60px;
    margin-left: 30px;
  }
  .chatwindow .toollist{
    position: absolute;
    right: 5px;
    top: 5px;
  }
  .chatwindow .toollist li{
    display: flex;
    justify-content: center;
    align-items: center;
    width: 28px;
    height: 20px;
    float: left;
  }
  .chatwindow .toollist img{
    width: 15px;
  }
  .toollist #toolmore{
    position: absolute;
    right: 0px;
    top: 28px;
  }
  .chatwindow .chatroom{
    width: 540px;
    height: 360px;
    border-bottom: 1px solid #e7e7e7;
  }
</style>
