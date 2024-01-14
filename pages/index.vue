import Axios from '~/components/Axios.vue';
<template>
  <div id="app">
    <h1 class="title">アプリ名</h1>
    <input type="text" v-model="newItem" class="white-text" />
    <form v-on:submit.prevent>
      <button v-on:click="addItem">add</button>
    </form>
    <ul>
      <li v-for="(todo, index) in todos" :key="index">
        {{ todo.item }}
        <button v-on:click="deleteItem(index)">delete</button>
      </li>
    </ul>
    <h2 class="subtitle">アプリ名</h2>
    <Axios />
  </div>
</template>
<script>
import Axios from "~/components/Axios.vue";

export default {
  data() {
    return {
      newItem: "",
      todos: [],
    };
  },
  methods: {
    addItem: function () {
      if (this.newItem.trim()) {
        var todo = {
          item: this.newItem,
        };
        this.todos.push(todo);
        this.newItem = ""; // 入力フィールドをクリア
      }
    },
    deleteItem: function (index) {
      this.todos.splice(index, 1);
    },
  },
  components: { Axios },
};
</script>

<style>
.white-text {
  color: white;
}
</style>
