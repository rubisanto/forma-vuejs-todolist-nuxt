<template>
  <div>
    <h2>Vous êtes sur un post unique !</h2>
    <!-- <h2>Le post numéro {{ article.id }}</h2>
    <hr>
    <h3>{{ article.title }}</h3>
    <p>{{ article.body }}</p> -->
  </div>
</template>
<!--
<script lang="ts">
interface Post {
  userId: number;
  id: number;
  title: string;
  body: string;
}

export default {
  async asyncData({ params }) {
    const id = params.id;
    const response = await fetch(`https://jsonplaceholder.typicode.com/posts/${id}`);
    const article: Post = await response.json();
    return { article };
  }
}
</script> -->
