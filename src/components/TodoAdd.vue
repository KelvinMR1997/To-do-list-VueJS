<template>
  <div id="add-container">
    <form @submit="addTodo">
      <input
        type="text"
        v-model="title"
        placeholder="Presiona ENTER  para guardar!"
      />
    </form>
  </div>
</template>

<script>
function capitalizeFirstLetter(string) {
      return string.charAt(0).toUpperCase() + string.slice(1);
    }
import { uuid } from "vue-uuid";
export default {

  name: "TodoAdd",
  data() {
    return {
      title: "",
    };
  },
  methods: {
     
    addTodo(e) {
      e.preventDefault();
      const newTodo = {
        id: uuid.v4(),
        // title: this.title,
        title: capitalizeFirstLetter(this.title),
        completed: false,
      };
      this.title = "";
      this.$emit("add-todo", newTodo);
    },
   
  },
};
</script>

<style scoped>
#add-container {
  padding: 10px;
}
input {
  padding: 10px;
  outline: none;
  border: solid 1px #ccc;
  width: 100%;
}
</style>