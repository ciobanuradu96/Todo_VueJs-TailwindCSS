<template>
  <div class="flex flex-col items-center m-auto mt-24 text-center">
    <p class="font-bold text-4xl text-red-400">To Do</p>
    <div class="text-right mr-12 mt-2 text-red-300 text-md m-auto">
      {{ totalChar }}/{{ charLimit }}
    </div>
    <div class="flex flex-row items-center m-auto">
      <textarea
        id="newTodo"
        cols="40"
        rows="2"
        class="mx-4 mb-4 mt-2 rounded-2xl text-2xl py-1 px-2 shadow-md bg-red-50"
        v-model="newTodo"
        @keyup.enter="addTodo(newTodo)"
      ></textarea>
      <button
        type="button"
        class="bg-red-500 px-3 py-1 shadow-md rounded-3xl text-xl font-extrabold text-center font-mono text-white hover:text-red-500 hover:bg-white"
        @click="addTodo(newTodo)"
      >
        +
      </button>
    </div>
    <TodoItem
      v-for="(todoItem, index) in todoList"
      :key="index"
      :todoItem="todoItem"
      :index="index"
      @delete="deleteTodo"
    />
  </div>
</template>

<script>
import TodoItem from "./TodoItem.vue";
export default {
  components: {
    TodoItem,
  },
  data() {
    return {
      newTodo: "",
      todoList: [],
      charLimit: 80,
    };
  },
  computed: {
    totalChar: function () {
      return this.newTodo.length;
    },
  },
  watch: {
    totalChar: function (newValue) {
      if (newValue > this.charLimit) {
        this.newTodo = this.newTodo.slice(
          0,
          -(this.totalChar - this.charLimit)
        );
      }
    },
  },
  methods: {
    addTodo(newTodo) {
      this.todoList.unshift(newTodo);
      this.newTodo = "";
      this.totalChar = 0;
      this.disabled = 0;
    },
    deleteTodo(index) {
      this.todoList.splice(index, 1);
    },
  },
};
</script>

<style>
</style>