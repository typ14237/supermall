<template>
  <div class="tabber-items" @click="itemClick">
    <div v-if="!isActive"><slot name='items-icon'></slot></div>
    <div v-else><slot name='items-icon-active'></slot></div>
    <div :style="activeStyle"><slot name='items-text'></slot></div>
  </div>
</template>

<script>
export default {
  name:"TabbarItem",
  props: {
    path:String,
    activeColor:{
      type:String,
      default:'#ff5777'
    }
  },
  data() {
    return {
      // isActive:true
    }
  },
  computed: {
    // 直接当做普通属性调用不加括号
    // 任何data中数据变化立即重新计算
    // 计算属性会缓存
    isActive(){
      return this.$route.path.indexOf(this.path) !==-1
    },
    activeStyle(){
      return this.isActive ? {color:this.activeColor}:{}
    }
  },
  methods: {
    itemClick(){
      this.$router.replace(this.path)
    }
  },
};
</script>
<style scoped>
.tabber-items{
  /* 文字居中 */
  text-align: center;
  /* 均等分弹性框 */
  flex: 1;
  /* 一般的tabber高度都为49 */
  height: 49px;
  font-size: 14px;
}
.tabber-items img{
  /* 设置图片大小 */
  width: 24px;
  height: 24px;
  /* 边框分开 */
  margin-top: 3px;
  /* 去除文字与图片之间的空隙 */
  vertical-align: middle;
  /* 自己定义图片和文字之间的空隙 */
  margin-bottom: 2px;
}
.active{
  color: #ff5777;
}
</style>