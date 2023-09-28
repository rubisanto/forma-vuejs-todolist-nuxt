<template>
  <div>
    <h1 class="center">TodoList en Vue.Js</h1>
    <ul>
      <li
      v-for="(todo, index) in todos"
      :key="index" >
        {{ todo.text }}
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
