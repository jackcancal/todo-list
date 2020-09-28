<template>
  <div id="app">
    <todo-list></todo-list>
  </div>
</template>

<script>
import TodoList from "@/components/TodoList";

export default {
  name: 'App',
  components: {
    TodoList,
  }
}
</script>
<style>
*{
  padding: 0;
  margin: 0;
}
</style>
