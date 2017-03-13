<template>
  <div class="header">
    <div style="display: flex">
      <div class="avatar">
        <img :src="seller.avatar" width="64" height="64"/>
      </div>
      <div>
        <span @click="showDetail">{{seller.name}}</span>
        <p>{{seller.description}}</p>
        <div v-if="seller.supports">
          <!--<span v-for="item in seller.supports">{{item.type}}</span>-->
          <!--<p v-for="item in seller.supports">{{item.type + 1}}.{{item.description}}</p>-->
          <p>优惠：{{seller.supports[0].description}}</p>
        </div>
        <p>sellCount:{{seller.sellCount}}</p>
        <p  @click="showDetail">公告：{{seller.bulletin}}</p>
        <div v-show="detailShow" class="detail">
          <div class="detail-wrapper clearfix">
            <div class="detail-main">
              <!--这是内容 区块-->
              <h1 @click="showDetail">{{seller.name}}</h1>
              <div v-if="seller.supports">
                <p v-for="item in seller.supports">{{item.type + 1}}.{{item.description}}</p>
                <star :size="48" score="4"></star>
              </div>
            </div>
          </div>
          <div class="detail-close" @click="detailClose">
            <!--<p>关闭</p>-->
            <i class="icon-close"></i>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script type="text/ecmascript-6">
  import star from '../star/star.vue'
  export default{
    name: 'header',
    props: {
      seller: {
        type: Object
      }
    },
    components:{
      star
    },
    data() {
      return {
        detailShow: false
      }
    },
    methods: {
      showDetail(){
        this.detailShow = true;
      },
      detailClose(){
        this.detailShow = false;
      },
    }
  }
</script>
<style>
  @import "../../common/style/style.css";
  .detail{
    position: absolute;
    z-index: 100;
    width: 100%;
    height: 100%;
    overflow: auto;
    background:rgba(7,17,27,0.8) ;
    top:0;
    left: 0;
    color: white;
  }
  .detail-wrapper{
    min-height: 100%;
    width: 100%;
    text-align: center;
  }
  .detail-main{
    margin-top: 64px;
    padding-bottom:64px ;
  }
  .clearfix{
    display :inline-block;
  }
  .clearfix :after{
    display: block;
    content: ".";
    height: 0;
    line-height: 0;
    clear:both;
    visibility: hidden;
  }
  .detail-close{
    position: relative;
    width: 32px;
    height: 32px;
    margin: -64px auto 0 auto;
    font-size: 32px;
  }
  /*清除浮动*/
</style>
<!--<style lang='stylus' rel='stylesheet/stylus'>-->
<!--</style>-->

