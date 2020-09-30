<script>
import AddToDo from "./components/AddToDo";
import Todos from "./components/Todos";
import Footer from "./components/Footer";

import { mapGetters } from "vuex";
export default {
  name: "App",
  components: {
    AddToDo,
    Todos,
    Footer,
  },

  computed: {
    ...mapGetters(["filteredTodos"]),
  },
};
</script>

<template>
  <div class="container">
    <AddToDo />
    <Todos :todos="filteredTodos" />
    <Footer :todos="filteredTodos" />
  </div>
</template>

<style>
*,
*::before,
*::after {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

body {
  font-size: 14px;
  font-family: Arial, Helvetica, sans-serif;
  line-height: 1.4;
  margin: auto;
  background-color: #f5f5f5;
}

.container {
  width: 500px;
  background: #fff;
  margin: 130px auto;
  position: relative;
  box-shadow: 0 2px 4px 0 rgba(0, 0, 0, 0.2), 0 25px 50px 0 rgba(0, 0, 0, 0.1);
}
</style>
