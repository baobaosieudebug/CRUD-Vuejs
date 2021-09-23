<template>
  <div class="add-todo">
    <input type="text" placeholder="Add a new task" v-model="task">
    <input type="submit" value="Add Task" class="add-btn" @click="addTodo">
  </div>

</template>

<script>
import { uuid } from "vue-uuid";
export default {
  name:"AddTodo",
  data() {
    return {
    task:'',
  }
},
  methods: {
     addTodo() {
       const data = {id:uuid.v4(),title:this.task,completed:false}
       this.$emit('inputData', data);
     }
  }
}
</script>

<style scoped>

.add-todo input[type='text'] {
  padding: 10px;
  cursor: pointer;
  margin: 10px;
  border-radius: 4px;
  width: 65%;
  background: rgb(240, 240, 240);
  color: black;
}

.add-todo input[type='submit'] {
  padding: 10px;
  cursor: pointer;
  margin: 10px 0;
  border-radius: 4px;
  background: rgb(240, 240, 240);
  color: black;
}
</style>
