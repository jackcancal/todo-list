<template>
  <div>
    <header class="header">
      <div class="header_inner">
        <div>TodoList</div>
        <el-input
            size="mini"
            v-model="inputValue"
            placeholder="添加Todo"
            @keypress.enter.native="addTodo"
        ></el-input>
      </div>
    </header>
    <main class="main">
      <div class="warp">
        <list-header :num="doingList.length"></list-header>
        <todo
            v-for="(item,index) in doingList"
            :name="item.name"
            :key="index"
            @checkinTodo="checkinDoingTodo($event, index, 'doingList')"
            @deleteTodo="deleteTodo(index, 'doingList')"
        />
        <list-header title="已经完成" :num="doneList.length"></list-header>
        <todo
            v-for="(item,index) in doneList"
            :name="item.name"
            :key="index+'doneList'"
            active
            @checkinTodo="checkinDoingTodo($event, index, 'doneList')"
            @deleteTodo="deleteTodo(index, 'doneList')"
        />
      </div>
    </main>
  </div>
</template>

<script>
import ListHeader from "@/components/ListHeader";
import Todo from "@/components/Todo";
export default {
  name: "TodoList",
  components: {Todo, ListHeader},
  data(){
    return {
      inputValue: '',
      doingList: [], //正在进行的TODO
      doneList: [], //已经完成的TODO
    }
  },
  methods:{
    // 添加一个todo
    addTodo(){
      if (!this.inputValue) return //非空判断
      this.doingList.push({name:this.inputValue})
      this.inputValue = ''
    },
    // 完成正在进行的TODO
    checkinDoingTodo(name,index,listName){
      const reverseListName = {
        'doingList': 'doneList',
        'doneList': 'doingList',
      }
      this[listName].splice(index,1)
      this[reverseListName[listName]].push({name})
    },
    // 删除一个todo
    deleteTodo(index, listName){
      this[listName].splice(index,1)
    }
  }
}
</script>

<style lang="scss" scoped>
.header{
  height: 60px;
  background-color: #333;
  display: flex;
  align-items: center;
  justify-content: center;
}
.header_inner{
  width: 600px;
  display: flex;
  align-items: center;
  justify-content: space-between;
  div:first-of-type{
    color: aliceblue;
    font-size: 20px;
  }
  /deep/.el-input{
    width: 300px;
    color: #000;
    ::placeholder{
      color: #000;
    }
  }
}
.main{
  min-height: calc(100vh - 60px);
  background-color: rgb(198, 198, 198);
  .warp{
    width: 600px;
    margin: 0 auto;
  }
}
</style>