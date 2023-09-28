<template>
  <div>
    <nuxt-link to="/">Home</nuxt-link>
    <nuxt-link to="/about">About</nuxt-link>
    <h1>Les articles de blog</h1>
    <hr>
    <ul>
      <li v-for="(article) in allArticles" :key="article.id">
        <nuxt-link :to="`/blog/${article.id}`">
        <div class="card m-2">
          <h3>{{ article.title }}</h3>
        </div>
      </nuxt-link>
      </li>
    </ul>

  </div>
</template>

<script lang="ts">

interface Post {
  userId: number;
  id: number;
  title: string;
  body: string;
}


export default {
  name: 'BlogPage',
  data () {
    return {
      allArticles: [] as Post[]
    }
  },
  created() {
    this.getAllArticles().catch(error => console.log(error));
  },
  methods: {
    async getAllArticles(){
      const response = await fetch('https://jsonplaceholder.typicode.com/posts');
      const blogPosts = await response.json();

      for(const article of blogPosts){
        this.allArticles.push(article);
      }
    }
  }
}

</script>

<style scoped>
</style>
