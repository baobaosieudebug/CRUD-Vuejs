<template>
  <div class="edit-todo">
    <input type="text" placeholder="Edit a new task" v-model="task">
    <input type="submit" value="Edit Task" class="edit-btn" @click="editTodo">
  </div>

</template>

<script>
export default {
  name:"EditTodo",
  data() {
    return {
      task:'',
    }
  },
  methods: {
    editTodo() {
      this.$emit('editTask', this.task);
    }
  }
}
</script>

<style scoped>

.edit-todo input[type='text'] {
  padding: 10px;
  cursor: pointer;
  margin: 10px;
  border-radius: 4px;
  width: 65%;
  background: rgb(240, 240, 240);
  color: black;
}

.edit-todo input[type='submit'] {
  padding: 10px;
  cursor: pointer;
  margin: 10px 0;
  border-radius: 4px;
  background: rgb(240, 240, 240);
  color: black;
}
</style>
