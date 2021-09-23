<template>
  <div id="app">
    <Navbar :total="total"/>
    <TodoList @totalTask="totalTask" />
  </div>
</template>

<script>
import Navbar from "./components/Navbar";
import TodoList from "./components/TodoList";

export default {
  name: 'App',
  components: {
    Navbar,
    TodoList,
  },
  data(){
    return {
      total:2,
    }
  },
  methods: {
    totalTask(updatedTotal){
     this.total = updatedTotal
    }
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  background: rgb(219, 219, 219);
  margin: 20px auto;
  width: 90%;
  max-width: 800px;
}
</style>
