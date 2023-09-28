<template>
  <div class="container">
    <h1 class="text-center mt-5 mb-4">TodoList en Vue.Js</h1>
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
        ] as {text : string}[]
      }
  },
  methods:{
    deleteTodo(index: number){
      this.todos.splice(index, 1);
    }
  }
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
