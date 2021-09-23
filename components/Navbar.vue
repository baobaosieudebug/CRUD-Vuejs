<template>
  <div class="navbar">
    <h1>Project todo list</h1>
    <ul>
      <li>Home</li>
      <li>About</li>
      <li>Total todos: {{total}}</li>
    </ul>
  </div>

</template>

<script>
export default {
 name: 'Navbar',
  props: {
   total: Number,
  },
}
</script>

<style>
.navbar {
  padding: 5px;
  text-align: center;
  background: rgb(240, 240, 240);
  color: black;
}

.navbar ul {
  display: flex;
  justify-content: space-around;
  align-items: center;
  list-style: none;
  padding: 0;
}

</style>
