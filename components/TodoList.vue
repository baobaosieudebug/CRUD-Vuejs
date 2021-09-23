<template>
  <div class="todo-list">
    <div v-if="!isEdited">
      <AddTodo @inputData="addTask"/>
    </div>
    <div v-else>
      <EditTodo @editTask="updateTask" />
    </div>

    <ul>
      <li v-for="todo in todos" :key="todo.id">{{todo.title}}
          <button @click="editTask(todo)">Edit</button>
          <button @click="deleteTask(todo)">Delete</button>
      </li>
    </ul>
  </div>

</template>

<script>
import AddTodo from "./AddTodo";
import EditTodo from "./EditTodo";
import { uuid } from "vue-uuid";
export default {
  name: 'TodoList',
  components:{EditTodo, AddTodo},
  data() {
    return {
      tempMessage: '',
      isEdited: false,
      props: ["update"],
      todos: [
        {id: uuid.v4(), title: 'VIEC 1', completed: false},
        {id: uuid.v4(), title: 'VIEC 2', completed: false},
      ]
    }
  },
  methods: {
    addTask(task) {
      this.todos.push(task);
      this.$emit('totalTask', this.todos.length);
    },

    editTask(index,task){
      this.index = index;
      this.task = task;
      this.isEdited = true;
    },

    updateTask(task){
      this.task = task;
      this.todos.forEach(task => {
        if(task.id === this.index.id){
          task.title = this.task;
        }
      });
    },

    deleteTask(index,task){
      this.index = index;
      this.task = task;
     this.todos = this.todos.filter(task => task.id !== this.index.id)
      this.$emit('totalTask', this.todos.length);
    }
  }
}
</script>

<style scoped>
.todo-list ul {
  padding: 0 10px 10px 10px;
  list-style-type: none;
}

.todo-list li {
  padding: 10px;
  cursor: pointer;
  margin: 10px 0;
  border-radius: 4px;
  background: rgb(240, 240, 240);
  color: black;
}
.todo-list button {
  padding: 10px;
  cursor: pointer;
  margin: 10px 0;
  border-radius: 4px;
  background: rgb(240, 240, 240);
  color: black;
}

.todo-list li input[type='checkbox'] {
  -ms-transform: scale(2); /* IE */
  -moz-transform: scale(2); /* FF */
  -webkit-transform: scale(2); /* Safari and Chrome */
  -o-transform: scale(2); /* Opera */
  transform: scale(2);
  padding: 10px;
  float: right;
}
</style>
