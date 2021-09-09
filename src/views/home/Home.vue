<template>
  <div id="home">
    <nav-bar class="home-nav">
      <div slot="center">购物街</div>
    </nav-bar>
    <home-swiper :banner="banner"></home-swiper>
    <home-recommend-view :recommend="recommend" />
    <home-feature-view />
    <tab-control class="tab-control"
                 :title="['流行', '新款', '精选']"
                 @tabClick="tabClick" />
    <goods-list :goods="showGoods"></goods-list>
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
    </ul>
  </div>
</template>

<script>
// 公共组件
import NavBar from "components/common/navbar/NavBar";
import TabControl from "components/content/TabControl.vue";
// 子组件
import HomeSwiper from "./childComps/HomeSwiper.vue";
import HomeRecommendView from "./childComps/HomeRecommendView.vue";
import HomeFeatureView from "./childComps/HomeFeatureView.vue";
import GoodsList from 'components/content/goods/GoodsList';
// 导入网络中响应数据的方法
import { getHomeMultidata, getHomeGoods } from "network/home";

export default {
  name: "Home",
  components: {
    NavBar,
    TabControl,
    HomeSwiper,
    HomeRecommendView,
    HomeFeatureView,
    GoodsList,
  },
  data () {
    return {
      // result:null,//查看有几种数据
      banner: [],
      recommend: [],
      keywords: [],
      dKeyword: [],
      goods: {
        "pop": {
          page: 0,
          list: [],
        },
        "new": {
          page: 0,
          list: [],
        },
        "sell": {
          page: 0,
          list: [],
        },
      },
      currentType: "pop"
    };
  },
  computed: {
    showGoods () {
      return this.goods[this.currentType].list
    }
  },
  created () {
    // 一般不会在生命周期函数中写具体逻辑，具体逻辑一般放在methods中，然后再直接使用这个方法
    // 这个this一定得要，因为是调用methods中的方法，否则会调用导入的方法
    // 请求多个数据
    this.getHomeMultidata();
    // 请求商品信息
    this.getHomeGoods("pop");
    this.getHomeGoods("new");
    this.getHomeGoods("sell");
  },
  methods: {
    /**
     * 事件监听相关的方法
     */
    tabClick (index) {
      switch (index) {
        case 0:
          this.currentType = 'pop'
          break;
        case 1:
          this.currentType = 'new';
          break;
        case 2:
          this.currentType = 'sell';
          break;
      }
    },
    /*
      网络请求相关的方法 
     */
    // 为什么要起同样的名字呢，这是为了避免命名污染和方便知道是哪个方法(和java中的重载类似)
    getHomeMultidata () {
      // 1.请求多个数据
      getHomeMultidata()
        .then((result) => {
          // this.result=result
          this.banner = result.data.banner.list;
          this.recommend = result.data.recommend.list;
          this.keywords = result.data.keywords;
          this.dKeyword = result.data.dKeyword;
        })
        .catch((err) => {
          console.log(err);
        });
    },
    getHomeGoods (type) {
      const page = this.goods[type].page + 1;
      getHomeGoods(type, page).then((res) => {
        this.goods[type].list.push(...res.data.list);
        this.goods[type].page += 1;
      });
    },
  },
};
</script>
<style scoped>
#home {
  padding-top: 44px;
}
.home-nav {
  background-color: var(--color-tint);
  color: #fff;
  position: fixed;
  left: 0;
  right: 0;
  top: 0;
  z-index: 2;
}
.tab-control {
  /* 当下滑到设置的的位置(44px)时，该position属性会改为fixed，并将该组件固定 */
  position: sticky;
  top: 44px;
  z-index: 9;
}
</style>