<template>
  <div class="container">
    <h2>
      <span>To Do</span>
      <span class="mask-num">{{ todos.length }}</span>
    </h2>
    <div v-for="(todo, index) in todos" :key="index">
      <ul class="mask-list">
        <li>
          <div>
            <input
              type="checkbox"
              @click="
                checked(todo.id);
                $emit('delTodo', todo.id);
              "
            />
            <span>{{ todo.text }}</span>
          </div>
          <button class="btn-remove" @click="$emit('delTodo', todo.id)">
            REMOVE
          </button>
        </li>
      </ul>
    </div>

    <h2>
      <span>Done</span>
      <span class="mask-num">
        {{ done_todos.length }}
      </span>
    </h2>
    <div v-for="done_todo in done_todos" :key="done_todo.id">
      <ul class="mask-list complete-list">
        <li>
          <div>
            <input type="checkbox" checked />
            <span>
              {{ done_todo.text }}
            </span>
          </div>
          <button class="btn-remove">REMOVE</button>
        </li>
      </ul>
    </div>
  </div>
</template>

<script>
export default {
  props: ["todos"],
  data() {
    return {
      done_todos: [],
    };
  },
  computed: {},
  methods: {
    checked(id) {
      this.done_todos.push(this.todos[id]);
    },
  },
};
</script>

<style>
</style>