<template>
  <div class="home">
    <div class="container">
      <AddTodo />
      <FilterTodos />
      <Todos />
    </div>
  </div>
</template>

<script>
// @ is an alias to /src
import Todos from "../components/Todos";
import AddTodo from "../components/AddTodo";
import FilterTodos from "../components/FilterTodos";

export default {
  name: "Home",
  components: {
    Todos,
    AddTodo,
    FilterTodos
  }
};
</script>

<style>
.container {
  max-width: 1100px;
  margin: auto;
  overflow: hidden;
  padding: 0 2rem;
}
</style>
