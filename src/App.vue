<template>
  <div id="app">
    <div class="header">
      <v-header class="header" :seller="seller"></v-header>
    </div>
    <div class="tab">
      <div class="tab-item">
        <!--<a v-link="{path:'/goods'}">商品</a>-->
        <router-link to="/goods" class="routerclass">商品</router-link>
      </div>
      <div class="tab-item">
        <!--<a v-link="{path:'/ratings'}">评论</a>-->
        <router-link to="/ratings" class="routerclass">评论</router-link>
        </div>
      <div class="tab-item">
        <!--<a v-link="{path:'/seller'}">商家</a>-->
        <router-link to="/seller" class="routerclass">商家</router-link>
        </div>
    </div>
    <!--<div class="content">-->
      <!--i am content-->
    <!--</div>-->
    <router-view></router-view>
    </div>
  </div>
</template>

<script type="text/ecmascript-6">
  import headers from './components/header/haeder.vue'
  const ERR_OK = 0;
export default {
  name: 'app',
  data(){
    return {
      seller:{}
    }
  },
  created(){
    this.$http.get('/api/seller').then((response) => {
      response =response.body;
      if(response.errno === ERR_OK){
        this.seller = response.data;
        console.log(this.seller);
      }else{

      }
    });
  },
  components: {
    'v-header':headers
  },
}
</script>
<style>
  /*@import './common/style/style.css';*/
  #app .tab{
    display: flex;
    width: 100%;
    height: 40px;
    line-height: 40px;
  }
  #app .tab .tab-item{
    flex: 1;
    text-align: center;
  }
  .routerclass{
    color: black;
    text-decoration: none;
  }
  .tab .tab-item >a{
    display: block;
    font-size: 14px;
  }
  .tab .tab-item >a :active{
    color: red;
  }

</style>
<!--<style lang="stylus" rel="stylesheet/stylus">-->
<!--</style>-->
