<script>
import { mapMutations } from "vuex";
export default {
  name: "AddToDo",
  methods: {
    ...mapMutations(["addTodo"]),

    handleKeyDown(e) {
      if (e.key === "Enter") {
        const title = e.target.value;
        this.addTodo(title);
        e.target.value = "";
      }
    },
  },
};
</script>

<template>
  <header>
    <h1 class="title">todos</h1>
    <input
      class="new-todo"
      placeholder="What needs to be done?"
      @keydown="handleKeyDown"
    />
  </header>
</template>

<style scoped>
.title {
  position: absolute;
  top: -155px;
  width: 100%;
  font-size: 100px;
  font-weight: 100;
  text-align: center;
  color: rgba(175, 47, 47, 0.15);
}
.new-todo {
  position: relative;
  margin: 0;
  width: 100%;
  font-size: 24px;
  font-family: inherit;
  font-weight: inherit;
  line-height: 1.4em;
  border: 0;
  color: inherit;
  padding: 6px;
  border: 1px solid #999;
  box-shadow: inset 0 -1px 5px 0 rgba(0, 0, 0, 0.2);
  box-sizing: border-box;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
}

.new-todo {
  padding: 16px 16px 16px 60px;
  border: none;
  background: rgba(0, 0, 0, 0.003);
  box-shadow: inset 0 -2px 1px rgba(0, 0, 0, 0.03);
}
.new-todo:focus {
  outline: none;
}
</style>
