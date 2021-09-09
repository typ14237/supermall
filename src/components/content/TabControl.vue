<!--
 * @Author: your name
 * @Date: 2021-08-02 11:50:48
 * @LastEditTime: 2021-09-02 11:11:16
 * @LastEditors: Please set LastEditors
 * @Description: In User Settings Edit
 * @FilePath: \exercise\supermall\src\components\content\TabControl.vue
-->
<template>
  <!-- 为什么不使用插槽呢，因为这里需要的插入的东西太少了，可以直接使用动态绑定，加父传子来完成 -->
  <div class="tab-control">
    <div v-for="(item,index) in title" :key="index"
     class="tab-control-item"
     :class="{active:index === currentIndex}" 
     @click="itemClick(index)">
      <span>{{item}}</span>
    </div>
  </div>
</template>

<script>
export default {
  name:"TabControl",
  props:{
    title:{
      type:Array,
      default(){
        return []
      }
    }
  },
  data() {
    return {
      currentIndex:0
    }
  },
  methods: {
    itemClick(index){
      this.currentIndex=index;
      this.$emit('tabClick',index)
    }
  },
}
</script>
<style scoped>
  .tab-control{
    display: flex;
    text-align: center;
    font-size: 16px;
    height: 40px;
    line-height: 40px;
    background-color: #fff;
  }
  .tab-control-item{
    flex: 1;

  }
  .active{
    color: var(--color-high-text);
    
  }
  .active span{
    border-bottom:3px solid var(--color-high-text);
    padding: 5px;
  }
</style>