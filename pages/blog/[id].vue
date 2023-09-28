<template>
  <div>
    <h2>Le post numéro {{ article.id }}</h2>
    <hr>
    <h3>{{ article.title }}</h3>
    <p>{{ article.body }}</p>
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
  name: 'BlogPostPage',
  data () {
    return {
      article : {} as Post
    }
  },
  created() {
    this.getTheArticle().catch(error => console.log(error));
  },
  methods: {
    async getTheArticle(){
      const response = await fetch(`https://jsonplaceholder.typicode.com/posts/${this.$route.params.id}`);
      console.log(this.$route.params.id);
      const blogPost = await response.json();

      this.article = blogPost;
    }
  }
}


</script>
