<!--
 * @Author: your name
 * @Date: 2021-08-10 13:49:55
 * @LastEditTime: 2021-09-02 10:32:02
 * @LastEditors: Please set LastEditors
 * @Description: In User Settings Edit
 * @FilePath: \supermall\src\components\content\goods\GoodsList.vue
-->
<template>
  <div class="goods">
    <goods-list-item v-for="item in goods" :key="item" :goodsItem="item" />
  </div>
</template>

<script>
import GoodsListItem from './GoodsListItem.vue';
export default {
  name:"GoodsList",
  components:{
    GoodsListItem,
  },
  props:{
    goods:{
      type:Array,
      default(){
        return []
      }
    }
  }
}

</script>
<style scoped>
  .goods {
    display: flex;
    flex-wrap: wrap;
    padding: 5px;
    justify-content: space-around;
  }

  .goods-list .item {
    width: 48%;
  }
</style>