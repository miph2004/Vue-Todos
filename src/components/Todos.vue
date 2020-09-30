<script>
import Todo from "./Todo";

import { mapMutations } from "vuex";

export default {
  name: "Todos",
  components: {
    Todo,
  },
  props: ["todos"],
  methods: {
    ...mapMutations(["toggleAllTodo"]),
  },
};
</script>

<template>
  <div class="main">
    <input class="toggle-all" />
    <label htmlFor="toggle-all" @click="toggleAllTodo"></label>
    <ul class="todo-list" v-for="todo in todos" :key="todo.id">
      <Todo :id="todo.id" :completed="todo.completed" :title="todo.title" />
    </ul>
  </div>
</template>

<style scoped>
.todo-list {
  margin: 0;
  padding: 0;
  list-style: none;
}

.todo-list li {
  position: relative;
  font-size: 24px;
  border-bottom: 1px solid #ededed;
}

.todo-list li .toggle {
  height: 40px;
  background: none;
  opacity: 0;
  text-align: center;
  width: 40px;
  height: auto;
  position: absolute;
  top: 0;
  bottom: 0;
  margin: auto 0;
  border: none;
  -webkit-appearance: none;
  appearance: none;
}

.todo-list li label {
  background-image: url("data:image/svg+xml;utf8,%3Csvg%20xmlns%3D%22http%3A//www.w3.org/2000/svg%22%20width%3D%2240%22%20height%3D%2240%22%20viewBox%3D%22-10%20-18%20100%20135%22%3E%3Ccircle%20cx%3D%2250%22%20cy%3D%2250%22%20r%3D%2250%22%20fill%3D%22none%22%20stroke%3D%22%23ededed%22%20stroke-width%3D%223%22/%3E%3C/svg%3E");
  background-repeat: no-repeat;
  background-position: center left;
  word-break: break-all;
  padding: 15px 15px 15px 60px;
  display: block;
  line-height: 1.2;
  transition: color 0.4s;
}

.todo-list li .toggle:checked + label {
  background-image: url("data:image/svg+xml;utf8,%3Csvg%20xmlns%3D%22http%3A//www.w3.org/2000/svg%22%20width%3D%2240%22%20height%3D%2240%22%20viewBox%3D%22-10%20-18%20100%20135%22%3E%3Ccircle%20cx%3D%2250%22%20cy%3D%2250%22%20r%3D%2250%22%20fill%3D%22none%22%20stroke%3D%22%23bddad5%22%20stroke-width%3D%223%22/%3E%3Cpath%20fill%3D%22%235dc2af%22%20d%3D%22M72%2025L42%2071%2027%2056l-4%204%2020%2020%2034-52z%22/%3E%3C/svg%3E");
}

.todo-list li {
  position: relative;
  font-size: 24px;
  border-bottom: 1px solid #ededed;
}

.todo-list li .destroy {
  display: none;
  position: absolute;
  top: 0;
  right: 10px;
  bottom: 0;
  width: 40px;
  height: 40px;
  margin: auto 0;
  font-size: 30px;
  color: #cc9a9a;
  margin-bottom: 11px;
  transition: color 0.2s ease-out;
}

.todo-list li:hover .destroy {
  display: block;
}

.todo-list li .destroy:after {
  content: "×";
}

.todo-list li .edit {
  display: none;
}

.todo-list li.editing:last-child {
  margin-bottom: -1px;
}
.todo-list li.editing {
  border-bottom: none;
  padding: 0;
}
.todo-list li.editing .edit {
  display: block;
  width: 90%;
  padding: 12px 16px;
  margin: 0 0 0 10%;
}

.todo-list li.completed label {
  color: #d9d9d9;
  text-decoration: line-through;
}

.toggle-all,
.todo-list li .toggle {
  background: none;
  cursor: pointer;
}

.toggle-all {
  text-align: center;
  border: none;
  opacity: 0;
  position: absolute;
}

.toggle-all + label {
  width: 60px;
  height: 34px;
  font-size: 0;
  position: absolute;
  top: -52px;
  left: -13px;
  -webkit-transform: rotate(90deg);
  transform: rotate(90deg);
  cursor: pointer;
}

.toggle-all + label:before {
  content: "❯";
  font-size: 22px;
  color: #e6e6e6;
  padding: 10px 27px 10px 27px;
}

.toggle-all:checked + label:before {
  color: #737373;
}

.main {
  position: relative;
  z-index: 2;
  border-top: 1px solid #e6e6e6;
}
</style>
