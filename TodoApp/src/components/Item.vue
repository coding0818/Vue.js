<template>
  <li v-for="(todo, index) in todos">
    <i class="fa fa-check" aria-hidden="true"></i>
    <span>{{ todo }}</span>
    <button @click="btnDelete(index)">삭제</button>
  </li>
</template>
<script>
import { useStore } from "vuex";

export default {
  name: "Item",
  props: {
    todo: String,
    no: Number,
  },
  setup(props) {
    const store = useStore();

    const todos = computed(() => store.getters.todos);

    const btnDelete = (index) => {
      console.log("index : " + index);
      store.dispatch("removeTodo", index);
    };
    return {
      todos,
      btnDelete,
    };
  },
};
</script>

<style scoped></style>
