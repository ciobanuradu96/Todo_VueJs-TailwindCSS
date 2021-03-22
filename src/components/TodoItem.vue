<template>
  <div class="flex items-center content-center w-96">
    <div
      class="flex-grow m-2 text-xl bg-red-400 text-white rounded-lg shadow-md cursor-pointer overflow-y-auto"
      @dblclick="deleteTodo(index)"
    >
      <p>{{ todoItem }}</p>
    </div>
    <div class="flex-none">
      <button
        class="bg-red-500 px-4 py-1 shadow-md rounded-3xl text-xl font-extrabold text-center font-mono text-white hover:text-red-500 hover:bg-white"
        @click="deleteTodo(index)"
      >
        -
      </button>
    </div>
  </div>
</template>

<script>
export default {
  props: ["todoItem", "index"],
  methods: {
    deleteTodo(index) {
      this.$emit("delete", index);
    },
  },
};
</script>

<style>
</style>