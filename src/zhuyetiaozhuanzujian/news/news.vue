<template>
    <div class="header3">
      <!--<tiaozhuanheader></tiaozhuanheader>-->
      <tiaozhuanheader>信工新闻眼</tiaozhuanheader>
      <div class="kong"></div>
        <div v-for="item in Newsone" :key="item._id">
        <!--<div class="news_box">-->
          <router-link :to="'/Newscontent?id='+item._id">
          <!--<router-link to="Newscontent">-->
            <div class="news_box">
              <div class="img_box">
                <!--<img src="../../img/dangbiao.png" alt="">-->
                <img :src="item.img" alt="">
              </div>
              <div class="right_box">
                <div class="top">
                  <!--<h3>河南日报：黄淮学院“党建e家”助力基层党建工作</h3>-->
                  <h3 v-text="item.title"></h3>
                </div>
                <div class="xia">
                  <div class="xia_zuo" v-text="item.updateTime"></div>
                  <!--<div class="xia_zuo">2018-04-12 11:08:52</div>-->
                  <div class="xia_you">
                    <i class="iconfont icon-yanjing"></i>
                    <!--<i class="iconfont icon-yanjing"></i>-->
                    <span class="you_right" >226</span>
                    <!--<span class="you_right" v-html="item.title"></span>-->
                  </div>
                </div>
              </div>
            </div>
          </router-link>
        </div>

        <!--<div class="news_box">-->
          <!--<router-link to="///">-->
            <!--<div>-->
              <!--<img src="../../img/dangbiao.png" alt="">-->
            <!--</div>-->
            <!--<div class="right_box">-->
              <!--<div class="top">-->
                <!--<h3>河南日报：黄淮学院“党建e家”助力基层党建工作</h3>-->
              <!--</div>-->
              <!--<div class="xia">-->
                <!--<span class="continet">2018-04-12 11:08:52</span>-->
                <!--<span class="xia_you">-->
                  <!--<i class="iconfont icon-yanjing"></i>-->
                  <!--<span class="you_right">226</span>-->
                <!--</span>-->
              <!--</div>-->
            <!--</div>-->
          <!--</router-link>-->
        <!--</div>-->

    </div>
</template>

<script>
  import tiaozhuanheader from '../../base/tiaozhuanheader.vue'
    export default {
        name: "news",
      components:{
        tiaozhuanheader
      },
      data(){
          return{
            Newsone:[]
          }
      },
      methods:{
        newsone(){
          // ,{type:"信工新闻眼"}
          this.$axios.get("Liebiao",{type:"2"}).then((res)=>{
            // console.log(res.data)
            this.Newsone=res.data.data
          })
        }
      },
      created(){
          this.newsone()
      },
    }
</script>
<style>
  .header3{
    width: 100%;
  }
  .kong{
    width: 100%;
    height: 50px;
  }
  .news_box{
    width: 100%;
    display: flex;
    border-bottom: 1px solid skyblue;
  }
  .news_box .img_box{
    width: 100px;
    height:100px;
  }
  .news_box .img_box img{
    width: 80px;
    height: 80px;
    padding: 10px;
  }
  .news_box .right_box{
    width: 100%;
  }
  .news_box .right_box .top{
    width: 100%;
  }
  .news_box .right_box .top h3{
    font-size: 16px;
    color: #585858;
    padding-top: 10px;
    padding-right: 5px;
  }
  .news_box .right_box .xia{
    width: 100%;
    font-size: 10px;
    color: #b3b3b3;
    margin-top: 30px;
    display: flex;
  }
  .news_box .right_box .xia i{
    padding-right: 5px;
  }
  .news_box .right_box .xia .xia_you{
     position: absolute;
     right: 0;
   }
  .news_box .right_box .xia .xia_you .you_right{
   padding-right: 10px;
  }
  .news_box .right_box .xia .xia_zuo{
    width: 80%;
  }
</style>
<style scoped>

</style>
