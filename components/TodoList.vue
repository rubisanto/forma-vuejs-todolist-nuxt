<template>
  <div class="container">
    <h1 class="text-center mt-5 mb-4">TodoList en Vue.Js</h1>
    <div class="mb-3">
      <input
        v-model="newTodo"
        type="text"
        class="form-control"
        placeholder="Ajouter une nouvelle tâche"
      />
      <button class="btn btn-primary mt-2" @click="addTodo(newTodo)">
        Ajouter la tache
      </button>
    </div>
    <ul class="list-group">
      <li
        v-for="(todo, index) in todos"
        :key="index"
        class="list-group-item d-flex justify-content-between align-items-center"
      >
        {{ todo.text }}
        <button
          class="btn btn-danger cursor-pointer"
          @click="deleteTodo(index)"
        >
          X
        </button>
      </li>
    </ul>

    <button class="btn btn-success mt-3" @click="passJson()">
      Transmettre en JSON
    </button>
    <div v-if="Jsonrevealed" class="mt-3">
      Les éléments JSON sont dans la console
    </div>
  </div>
</template>

<script lang="ts">
export default {
  name: 'TodoList',
  data() {
    return {
      todos: [
        { text: 'Learn JavaScript' },
        { text: 'Learn Vue' },
        { text: 'Build something awesome' },
      ] as { text: string }[],
      newTodo: '',
      Jsonrevealed: false,
    }
  },
  mounted() {
    // Charger les todos depuis le localStorage si disponibles
    const storeTodos = localStorage.getItem('todos')

    if (storeTodos) {
      this.todos = JSON.parse(storeTodos)
    }
  },
  methods: {
    deleteTodo(index: number) {
      this.todos.splice(index, 1)

      // sauvegarde dans le local storage
      localStorage.setItem('todos', JSON.stringify(this.todos))
    },
    addTodo(newTodo: string) {
      this.todos.push({ text: newTodo })
      this.newTodo = ''

      // sauvegarde dans le local storage
      localStorage.setItem('todos', JSON.stringify(this.todos))
    },
    passJson() {
      console.log(JSON.stringify(this.todos), 'JSON des todos')
      this.Jsonrevealed = true
    },
  },
}
</script>

<style scoped>
.center {
  text-align: center;
}

ul {
  padding: 0;
}

li {
  list-style-type: none;
  margin-bottom: 5px;
}
</style>
