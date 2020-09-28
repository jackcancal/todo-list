<template>
  <div class="todo">
    <div
        style="display: flex;align-items: center;justify-content: center;margin-left: 10px;"
        @click="checkinTodo"
    >
      <div class="checkbox" :class="{active}"></div>
      <div class="todo_name">{{name}}</div>
    </div>
    <img
        class="delete"
        src="../assets/delete.png"
        alt=""
        @click="deleteTodo"
    >
  </div>
</template>

<script>
export default {
  name: "Todo",
  props: {
    name: {
      type: String,
      default: ''
    },
    active:{
      type: Boolean,
      default: false
    }
  },
  methods:{
    checkinTodo(){
      this.$emit('checkinTodo', this.name)
    },
    deleteTodo(){
      this.$emit('deleteTodo',this.name)
    }
  }
}
</script>

<style lang="scss" scoped>
.todo{
  margin: 10px 0;
  width: 100%;
  height: 32px;
  background-color: #fff;
  box-sizing: border-box;
  display: flex;
  align-items: center;
  justify-content: space-between;
  border-radius: 3px;
  border-left: 5px solid #629A9C;
}
.checkbox{
  width: 26px;
  height: 26px;
  box-sizing: border-box;
  border-radius: 2px;
  border: 1px solid #ccc;
  margin-right: 10px;
  cursor: pointer;
  overflow: hidden;
  background-repeat: no-repeat;
  background-size: cover;
  background-position: center;
  &.active{
    background-image: url('../assets/checkbox.png');
    border: none;
  }
}
.delete{
  width: 20px;
  height: 20px;
  margin-right: 10px;
  cursor: pointer;
}
</style>