<template>
  <div  class="main">
    <div class="user">
      <div class="block">
        <el-avatar  class="avatar" :size="80" alt="头像"
                    :src="user.avatar ? baseURL+user.avatar : 'https://cube.elemecdn.com/3/7c/3ea6beec64369c2642b92c6726f1epng.png' "></el-avatar>
      </div>
      <div class="username">{{ this.user.username }}</div>
      <div class="email-info">
        <img src="@/assets/email.png" alt="邮箱" class="email-img">
        <div class="email-text">{{ this.user.email }}</div>
      </div>
    </div>
    <div class="information">
      <div style="position: absolute;left:12%">
        <div >文章</div>
        <div>{{articleNum}}</div>
      </div>
      <div style="position: absolute;left:45%">
        <div>标签</div>
        <div>{{tagNum}}</div>
      </div>
      <div style="position: absolute;left:78%">
        <div >点赞</div>
        <div style="font-size: medium;">{{likeNum}}</div>
      </div>
    </div>
  </div>
</template>

<script>
import axios from "axios";
import {id} from "html-webpack-plugin/lib/chunksorter";

export default{
  props:{
    user:Object,
    articleNum:String,
    tagNum:String,
    likeNum:String,
  },
  data() {
    return{
      baseURL:'http://localhost:8090/static/avatar/',
    }
  },

  created(){
    this.axios = axios.create({
      baseURL: 'http://localhost:8090', // 后端 API 的地址
      timeout: 5000 // 请求超时时间
    });

  },
  activated() {

  },
  mounted(){



  },
  methods:{
    errorHandler() {
      return true
    },
  }

}
</script>

<style scoped>
.main{
  position: relative;
  width: 300px;
  height: 250px;
  background-color: rgb(232, 236, 236);
  /*background-color: rgba(240, 248, 255, 0.74);*/
  opacity: 1;
  border-radius:15px;
  box-shadow: 0 4px 8px rgba(0, 0, 0, 0.3); /* 设置阴影效果 */
  transition: box-shadow 0.3s ease; /* 添加过渡效果 */
  transition: transform 0.3s ease; /* 添加过渡效果 */
}

.main:hover {
  box-shadow: 0 8px 16px rgba(0, 0, 0, 0.6); /* 悬浮时增加阴影效果 */
  transform: scale(1.02); /* 悬浮时微微放大 */
}

.avatar{
  position: absolute;
  width:50px;
  height: 50px;
  top: 30%;
  left: 50%; /* 距离左侧50% */
  transform: translate(-50%, -50%); /* 使用负边距将元素居中 */
}

.user{
  position: absolute;
  width:100%;
  height: 76%;
  top:0;
}

.email-info{
  position: absolute;
  width:100%;
  top:75%;
  height:40px;
}

.email-img{
  position: absolute;
  left:10%;
  width:30px;
  height:30px;
  margin-top:2px;
}
.email-text{
  position: absolute;
  width:80%;
  left:10%;
  margin-top:8px;
}

.username{
  position: absolute;
  top:65%;
  left: 50%; /* 距离左侧50% */
  transform: translate(-50%, -50%); /* 使用负边距将元素居中 */
}

.information{
  position: absolute;
  width:100%;
  height:24%;
  top:76%;
}


</style>
