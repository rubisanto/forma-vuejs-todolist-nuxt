<template>
<div>

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
