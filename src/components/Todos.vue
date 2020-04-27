<template>
  <div class="container">
    <h3>Todos</h3>
    <div class="legend">
      <span>Double click to mark as complete</span>
      <span>
        <span class="inc-box"></span> = INC
      </span>
      <span>
        <span class="com-box"></span> = COM
      </span>
    </div>
    <div class="todos">
      <div
        v-for="todo in allTodos"
        :key="todo.id"
        class="todo"
        :class="{'is-complete' : todo.completed}"
        @dblclick="ondblClick(todo)"
      >
        {{todo.title}}
        <font-awesome-icon icon="trash" @click="deleteTodo(todo.id)" />
      </div>
    </div>
  </div>
</template>

<script>
import { mapGetters, mapActions } from "vuex";

export default {
  name: "Todos",
  methods: {
    ...mapActions(["fetchTodos", "deleteTodo", "updateTodo"]),
    ondblClick(todo) {
      const updTodo = {
        id: todo.id,
        title: todo.title,
        completed: !todo.completed
      };

      this.updateTodo(updTodo);
    }
  },
  computed: mapGetters(["allTodos"]),
  created() {
    this.fetchTodos();
  }
};
</script>

<style>
.todos {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  grid-gap: 1rem;
}

.todo {
  border: 1px solid #ccc;
  background: #41b883;
  padding: 1rem;
  border-radius: 4px;
  text-align: center;
  position: relative;
  cursor: pointer;
}

svg {
  position: absolute;
  bottom: 10px;
  right: 10px;
  color: #ffffff;
  cursor: pointer;
}

.legend {
  display: flex;
  justify-content: space-around;
  margin-bottom: 1rem;
}

.inc-box {
  display: inline-block;
  width: 10px;
  height: 10px;
  background: #41b883;
}

.com-box {
  display: inline-block;
  width: 10px;
  height: 10px;
  background: #35495e;
}

.is-complete {
  background: #35495e;
  color: #ffffff;
}
</style>