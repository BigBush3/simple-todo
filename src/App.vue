<template>
  <div>
    <div class="header">
      <div class="container">
        <div class="logo">ToDo List</div>
        <div class="form">
          <input type="text" v-model="text" @keyup.enter="enterClicked()" />
          <button class="btn" @click="addTodo()">Add a new task</button>
        </div>
      </div>
    </div>
    <ToDo :todos="todos" @delTodo="removeTodo" />
  </div>
</template>

<script>
import ToDo from "./components/ToDo";

export default {
  components: {
    ToDo,
  },
  data() {
    return {
      todos: [],
      text: "",
      id: 0,
    };
  },
  methods: {
    addTodo() {
      if (this.text === "") {
        return;
      } else {
        this.todos.push({
          text: this.text,
          id: this.id,
        });
        this.id += 1;
      }
    },
    enterClicked() {
      if (this.text === "") {
        return;
      } else {
        this.todos.push({
          text: this.text,
          id: this.id,
        });
        this.id += 1;
        this.text = "";
      }
    },
    removeTodo(data) {
      this.todos.splice(data, 1);
    },
  },
  computed: {},
};
</script>

<style>
</style>
