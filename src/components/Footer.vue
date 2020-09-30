<script>
import { mapMutations } from "vuex";
export default {
  name: "Footer",
  props: ["todos"],
  data() {
    return {
      selectedAll: true,
      selectedActive: false,
      selectedCompleted: false,
    };
  },
  methods: {
    ...mapMutations(["clearCompleted", "mutateFilter"]),

    selected(id) {
      switch (id) {
        case "all":
          this.selectedAll = true;
          this.selectedActive = false;
          this.selectedCompleted = false;
          break;
        case "active":
          this.selectedAll = false;
          this.selectedActive = true;
          this.selectedCompleted = false;
          break;
        case "completed":
          this.selectedAll = false;
          this.selectedActive = false;
          this.selectedCompleted = true;
          break;
      }
    },
  },
};
</script>

<template>
  <footer class="footer">
    <span class="todo-count">
      <strong>{{ todos.filter((t) => !t.completed).length }} item left</strong>
    </span>
    <ul class="filters">
      <li
        :class="{ selected: selectedAll }"
        @click="
          mutateFilter({ filter: `SHOW_ALL` });
          selected(`all`);
        "
      >
        <a> All </a>
      </li>

      <li
        :class="{ selected: selectedActive }"
        @click="
          mutateFilter({ filter: `SHOW_ACTIVE` });
          selected(`active`);
        "
      >
        <a> Active </a>
      </li>

      <li
        :class="{ selected: selectedCompleted }"
        @click="
          mutateFilter({ filter: `SHOW_COMPLETED` });
          selected(`completed`);
        "
      >
        <a> Completed </a>
      </li>
    </ul>
    <button class="clear-completed" @click="clearCompleted()">
      Clear completed
    </button>
  </footer>
</template>

<style scoped>
button {
  margin: 0;
  padding: 0;
  border: 0;
  background: none;
  font-size: 100%;
  vertical-align: baseline;
  font-family: inherit;
  font-weight: inherit;
  color: inherit;
  -webkit-appearance: none;
  appearance: none;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  cursor: pointer;
}

.footer {
  color: #777;
  padding: 10px 15px;
  height: 40px;
  text-align: center;
  border-top: 1px solid #e6e6e6;
}

.footer:before {
  content: "";
  position: absolute;
  right: 0;
  bottom: 0;
  left: 0;
  height: 20px;
  overflow: hidden;
  box-shadow: 0 1px 1px rgba(0, 0, 0, 0.2), 0 8px 0 -3px #f6f6f6,
    0 9px 1px -3px rgba(0, 0, 0, 0.2), 0 16px 0 -6px #f6f6f6,
    0 17px 2px -6px rgba(0, 0, 0, 0.2);
}

.todo-count {
  float: left;
  text-align: left;
}

.filters {
  margin: 0;
  padding: 0;
  list-style: none;
  position: absolute;
  right: 0;
  left: 0;
}

.clear-completed,
html .clear-completed:active {
  float: right;
  position: relative;
  line-height: 20px;
  text-decoration: none;
  cursor: pointer;
}
.clear-completed:hover {
  text-decoration: underline;
}

.filters li.selected {
  border-color: rgba(175, 47, 47, 0.2);
}
.filters li {
  color: inherit;
  margin: 3px;
  padding: 3px 7px;
  text-decoration: none;
  border: 1px solid transparent;
  border-radius: 3px;
  cursor: pointer;
}

.filters li {
  display: inline;
}
</style>
