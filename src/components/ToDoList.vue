<template>
  <div id="ToDoList">
    <h1>Welcome to your to do list, {{user.username}}</h1>

    <form v-on:submit.prevent="this.addNewTodo">
      <label for="new-todo">Add a todo</label>
      <input
        v-model="this.$root.$data.newTodoText"
        id="new-todo"
        placeholder="E.g. Feed the cat"
      >
      <button>Add</button>
    </form>

    <ul>
      <li
        is="todo-item"
        v-for="(todo, index) in this.$root.$data.todos"
        v-bind:key="todo.id"
        v-bind:title="todo.title"
        v-on:remove="this.$root.$data.todos.splice(index, 1)"
      ></li>
    </ul>

    <router-link to="/">Psuedo Sign Out</router-link>
  </div>
</template>

<script>
  export default {
    name: 'to-do-list',
    data () {
      return {
        user: {
          username: 'User1'
        }
      }
    }
  }
</script>

<style scoped>
</style>
