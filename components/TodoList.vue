<template>
  <div class="container">
    <h1 class="text-center mt-5 mb-4">TodoList en Vue.Js</h1>
    <div class="mb-3">
      <input v-model="newTodo" type="text" class="form-control" placeholder="Add new task">
      <button  class="btn btn-primary mt-2" @click="addTodo(newTodo)" >Add Task</button>
    </div>
    <ul class="list-group">
      <li
        v-for="(todo, index) in todos"
        :key="index"
        class="list-group-item d-flex justify-content-between align-items-center">
        {{ todo.text }}
        <button class="btn btn-danger cursor-pointer" @click="deleteTodo(index)">X</button>
      </li>
    </ul>
  </div>
</template>



<script lang="ts">

export default {
  name: 'TodoList',
  data(){
      return{
        todos: [
          { text: 'Learn JavaScript' },
          { text: 'Learn Vue' },
          { text: 'Build something awesome' }
        ] as {text : string}[],
        newTodo: ''
      }
  },
    mounted() {
  // Charger les todos depuis le localStorage si disponibles
  const storeTodos = localStorage.getItem('todos');

  if (storeTodos) {
    this.todos = JSON.parse(storeTodos);

  }
},
  methods:{
    deleteTodo(index: number){
      this.todos.splice(index, 1);

      // sauvegarde dans le local storage
      localStorage.setItem('todos', JSON.stringify(this.todos));
    },
    addTodo (newTodo: string) {
      this.todos.push({ text: newTodo })
      this.newTodo = ''

      // sauvegarde dans le local storage
      localStorage.setItem('todos', JSON.stringify(this.todos));
    }
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
