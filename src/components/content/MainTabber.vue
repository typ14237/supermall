<template>
  <div id="main-tabber">
    <tabbar>
      <tabbar-item>
        <img slot="items-icon" src="../../assets/img/home.svg" alt="" />
        <img slot="items-icon-active" src="../../assets/img/home_active.svg" alt="" />
        <div slot="items-text">首页</div>
      </tabbar-item>
      <tabbar-item>
        <img slot="items-icon" src="../../assets/img/category.svg" alt="" />
        <img slot="items-icon-active" src="../../assets/img/category_active.svg" alt="" />
        <div slot="items-text">分类</div>
      </tabbar-item>
      <tabbar-item>
        <img slot="items-icon" src="../../assets/img/shopcart.svg" alt="" />
        <img slot="items-icon-active" src="../../assets/img/shopcart_active.svg" alt="" />
        <div slot="items-text">购物车</div>
      </tabbar-item>
      <tabbar-item>
        <img slot="items-icon" src="../../assets/img/profile.svg" alt="" />
        <img slot="items-icon-active" src="../../assets/img/profile_active.svg" alt="" />
        <div slot="items-text">我的</div>
      </tabbar-item>
    </tabbar>
  </div>
</template>

<script>
import Tabbar from "../common/tabber/Tabbar.vue";
import TabbarItem from "../common/tabber/TabbarItem.vue";
export default {
  name: "MainTabber",
  components: {
    Tabbar,
    TabbarItem,
  },
};
</script>
<style scoped>
</style>