<template>

<div>
  <nuxt-link to="/about">About</nuxt-link>
  <nuxt-link to="/blog">Blog</nuxt-link>
  <TodoList></TodoList>
</div>
</template>

<script lang="ts">
import Vue from 'vue'
import TodoList from '~/components/TodoList.vue';


export default Vue.extend({
    name: 'IndexPage',
    components: { TodoList }
})
</script>
