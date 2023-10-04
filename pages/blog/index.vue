<template>
  <div>
    <NuxtLink to="/">Home</NuxtLink>
    <NuxtLink to="/about">About</NuxtLink>
    <h1>Les articles de blog</h1>
    <hr />
    <ul>
      <li
        v-for="article in allArticles"
        :key="article.id"
        @mouseenter="consoleProporties(article)"
      >
        <NuxtLink :to="`/blog/${article.id}`">
          <div class="card m-2">
            <h3>{{ article.title }}</h3>
          </div>
        </NuxtLink>
      </li>
    </ul>
  </div>
</template>

<script lang="ts">
import Vue from 'vue'
interface Post {
  userId: number
  id: number
  title: string
  body: string
}

export default Vue.extend({
  name: 'BlogPage',
  data() {
    return {
      allArticles: [] as Post[],
    }
  },
  created() {
    this.getAllArticles().catch((error) => console.log(error))
  },
  methods: {
    async getAllArticles() {
      const response = await fetch('https://jsonplaceholder.typicode.com/posts')
      const blogPosts = await response.json()

      for (const article of blogPosts) {
        this.allArticles.push(article)
      }
      // console pour les id et le type
      //   for (const article of this.allArticles) {
      //   console.log("ID : " + article.id + "type : " + typeof(article.id));
      // }
    },
    consoleProporties(article: Post) {
      console.log('ID : ' + article.id + 'type : ' + typeof article.id)
    },
  },
})
</script>

<style scoped></style>
