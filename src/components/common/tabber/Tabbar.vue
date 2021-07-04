<template>
    <div id="tabbar">
      <slot></slot>
    </div>
</template>

<script>
export default {
  name:"Tabber"
}

</script>
<style scoped>
#tabbar {
  display: flex;
  position: fixed;
  background-color: #f6f6f6;
  bottom: 0;
  left: 0;
  right: 0;
  box-shadow: 0 -1px 1px rgba(100, 100, 100, 0.2);
}

</style>