<template>
  <div class="tabber-items">
    <div v-if="!isActive"><slot name='items-icon'></slot></div>
    <div v-else><slot name='items-icon-active'></slot></div>
    <div><slot name='items-text'></slot></div>
  </div>
</template>

<script>
export default {
  name:"TabbarItem",
  data() {
    return {
      isActive:false
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
</style>