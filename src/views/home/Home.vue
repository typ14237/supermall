<template>
  <div id="home">
    <nav-bar class="home-nav">
      <div slot="center">购物街</div>
    </nav-bar>
    <home-swiper :banner="banner"></home-swiper>
  </div>
</template>

<script>
import NavBar from 'components/common/navbar/NavBar'
import HomeSwiper from './childComps/HomeSwiper.vue'

import {getHomeMultidata} from 'network/home';

export default {
  name:"Home",
  components:{
    NavBar,
    HomeSwiper
  },
  data() {
    return {
      //result:null,//查看有几种数据
      banner:[],
      recommend:[],
      keywords:[],
      dKeyword:[]
    }
  },
  created() {
    // 1.请求多个数据
    getHomeMultidata().then((result) => {
      //this.result=result
      this.banner=result.data.banner.list
      this.recommend=result.data.recommend.list
      this.keywords=result.data.keywords
      this.dKeyword = result.data.dKeyword
    }).catch((err) => {
      console.log(err);
    });
  },
}

</script>
<style scoped>

  .home-nav{
    background-color:var(--color-tint) ;
    color: #fff;
  }
</style>