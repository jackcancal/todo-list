<template>
  <div class="list_header">
    <div>{{title}}</div>
    <div>{{num}}</div>
  </div>
</template>

<script>
export default {
  name: "ListHeader",
  props: {
    title: {
      type: String,
      default: '正在进行'
    },
    num: {
      type: Number,
      default: 0
    },
  }
}
</script>

<style lang="scss" scoped>
.list_header{
  height: 55px;
  display: flex;
  align-items: center;
  justify-content: space-between;
  div:first-of-type{
    font-size: 22px;
  }
  div:last-of-type{
    width: 20px;
    height: 20px;
    background-color: #e2e2f8;
    border-radius: 50%;
    display: flex;
    align-items: center;
    justify-content: center;
    font-size: 12px;
    font-weight: bold;
  }
}
</style>