<template>
  <div id="app">
    <h1 class="title">Vue 2 Todo App</h1>
    <div class="todo-input">
      <input
          v-model="newTodo"
          @keyup.enter="addTodo"
          placeholder="Enter a new todo"
          class="input-field"
      >
      <button @click="addTodo" class="add-button">Add Todo</button>
    </div>
    <ul class="todo-list">
      <li v-for="(todo, index) in todos" :key="index" class="todo-item">
        <span class="todo-text">{{ todo }}</span>
        <button @click="removeTodo(index)" class="remove-button">Remove</button>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  name: 'App',
  data() {
    return {
      newTodo: '',
      todos: []
    }
  },
  methods: {
    addTodo() {
      if (this.newTodo.trim()) {
        this.todos.push(this.newTodo.trim());
        this.newTodo = '';
      }
    },
    removeTodo(index) {
      this.todos.splice(index, 1);
    }
  }
}
</script>

<style scoped>
#app {
  font-family: Arial, sans-serif;
  max-width: 500px;
  margin: 0 auto;
  padding: 20px;
  box-shadow: 0 0 10px rgba(0,0,0,0.1);
  border-radius: 8px;
}

.title {
  color: #2c3e50;
  text-align: center;
}

.todo-input {
  display: flex;
  margin-bottom: 20px;
}

.input-field {
  flex-grow: 1;
  padding: 10px;
  font-size: 16px;
  border: 1px solid #ddd;
  border-radius: 4px 0 0 4px;
}

.add-button {
  padding: 10px 20px;
  font-size: 16px;
  background-color: #4CAF50;
  color: white;
  border: none;
  border-radius: 0 4px 4px 0;
  cursor: pointer;
}

.todo-list {
  list-style-type: none;
  padding: 0;
}

.todo-item {
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 10px;
  background-color: #f9f9f9;
  border-radius: 4px;
  margin-bottom: 10px;
}

.todo-text {
  flex-grow: 1;
}

.remove-button {
  padding: 5px 10px;
  background-color: #f44336;
  color: white;
  border: none;
  border-radius: 4px;
  cursor: pointer;
}
</style>