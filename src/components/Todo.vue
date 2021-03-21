<template>
  <div class="flex flex-col mx-auto mt-24 content-center text-center">
    <p class="font-bold text-4xl text-red-400">To Do</p>
    <div class="flex flex-row items-center">
      <textarea
        id="newTodo"
        cols="40"
        rows="2"
        class="m-4 rounded-2xl text-2xl shadow-md bg-red-50"
        v-model="newTodo"
      ></textarea>
      <button
        type="button"
        class="bg-red-500 px-3 py-1 shadow-md rounded-3xl text-xl font-extrabold text-center font-mono text-white hover:text-red-500 hover:bg-white"
        @click="addTodo(newTodo)"
      >
        +
      </button>
    </div>
    <div
      v-for="(todoItem, index) in todoList"
      :key="index"
      class="flex flex-row items-center mx-auto"
    >
      <div
        class="m-2 text-xl bg-red-400 text-white p-3 rounded-lg shadow-md w-96 min-w-min cursor-pointer"
      >
        {{ todoItem }}
      </div>
      <button
        class="bg-red-500 px-3 py-1 shadow-md rounded-3xl text-xl font-extrabold text-center font-mono text-white hover:text-red-500 hover:bg-white"
        @click="deleteTodo(index)"
      >
        -
      </button>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      newTodo: "test",
      todoList: [],
    };
  },
  methods: {
    addTodo(newTodo) {
      this.todoList.unshift(newTodo);
      this.newTodo = "";
    },
    deleteTodo(index) {
      this.todoList.splice(index, 1);
    },
  },
};
</script>

<style>
</style>