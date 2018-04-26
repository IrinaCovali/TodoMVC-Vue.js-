<template>
  <div class="main">
    <div class="flex-block mb20">
      <input
        v-model="newTodo"
        placeholder="New Todo"
        type="text"
        class="add flex-grow"
      >
      <button v-on:click="addNewTodo" class="button button-add">add</button>
    </div>
    <ul>
      <transition-group name="todo">
        <li
          v-for="(todo, index) in todos"
          v-bind:key="todo.id"
        >
          {{todo.title}}
          <button class="button button-delete" v-on:click="todos.splice(index, 1)">X</button>
        </li>
      </transition-group>
    </ul>
  </div>
</template>

<script>
export default {
  name: "App",
  data() {
    return {
      newTodo: "",
      todos: [
        {
          id: 1,
          title: "Lorem ipsum"
        },
        {
          id: 2,
          title:
            "Neque porro quisquam est qui dolorem ipsum quia dolor sit amet"
        }
      ],
      nextTodoId: 3
    };
  },
  methods: {
    addNewTodo: function() {
      if (!this.newTodo) {
        return;
      }

      this.todos.push({
        id: this.nextTodoId++,
        title: this.newTodo
      });
      this.newTodo = "";
    }
  }
};
</script>
