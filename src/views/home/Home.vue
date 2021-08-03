<template>
  <div id="home">
    <nav-bar class="home-nav">
      <div slot="center">购物街</div>
    </nav-bar>
    <home-swiper :banner="banner"></home-swiper>
    <home-recommend-view :recommend="recommend" />
    <home-feature-view />

    <tab-control class="tab-control" :title="['流行','新款','精选']" />
    <ul>
      <li>列表1</li>
      <li>列表2</li>
      <li>列表3</li>
      <li>列表4</li>
      <li>列表5</li>
      <li>列表6</li>
      <li>列表7</li>
      <li>列表8</li>
      <li>列表9</li>
      <li>列表10</li>
      <li>列表11</li>
      <li>列表12</li>
      <li>列表13</li>
      <li>列表14</li>
      <li>列表15</li>
      <li>列表16</li>
      <li>列表17</li>
      <li>列表18</li>
      <li>列表19</li>
      <li>列表20</li>
      <li>列表16</li>
      <li>列表17</li>
      <li>列表18</li>
      <li>列表19</li>
      <li>列表20</li>
      <li>列表16</li>
      <li>列表17</li>
      <li>列表18</li>
      <li>列表19</li>
      <li>列表20</li>
      <li>列表19</li>
      <li>列表20</li>
      <li>列表16</li>
      <li>列表17</li>
      <li>列表18</li>
      <li>列表19</li>
      <li>列表20</li>
      <li>列表16</li>
      <li>列表17</li>
      <li>列表18</li>
      <li>列表19</li>
      <li>列表20</li>
      <li>列表19</li>
      <li>列表20</li>
      <li>列表16</li>
      <li>列表17</li>
      <li>列表18</li>
      <li>列表19</li>
      <li>列表20</li>
      <li>列表16</li>
      <li>列表17</li>
      <li>列表18</li>
      <li>列表19</li>
      <li>列表20</li>
    </ul>
  </div>
</template>

<script>
// 公共组件
import NavBar from 'components/common/navbar/NavBar'
import TabControl from '../../components/content/TabControl.vue';
// 子组件
import HomeSwiper from './childComps/HomeSwiper.vue'
import HomeRecommendView from './childComps/HomeRecommendView.vue';
import HomeFeatureView from './childComps/HomeFeatureView.vue';
// 导入的方法
import {getHomeMultidata} from 'network/home';

export default {
  name:"Home",
  components:{
    NavBar,
    TabControl,
    HomeSwiper,
    HomeRecommendView,
    HomeFeatureView,
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
  #home{
    padding-top:44px;
  }
  .home-nav{
    background-color:var(--color-tint) ;
    color: #fff;
    position:fixed ;
    left: 0;
    right: 0;
    top: 0;
    z-index: 2;
  }
  .tab-control{
    /* 当下滑到设置的的位置(44px)时，该position属性会改为fixed，并将该组件固定 */
    position: sticky;
    top:44px;
  }
</style>