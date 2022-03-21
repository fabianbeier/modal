<template>
  <div class="m-12">
    <ul class="grid grid-cols-2 gap-5">
      <li v-for="post in posts" :key="post.id"><Card :content="post"/></li>
    </ul>
    <nuxt-child />
  </div>
</template>

<script>
import Card from "~/components/Card.vue";
export default {
    data() {
      return {
        posts: []
      }
    },
    async fetch() {
      this.posts = await fetch(
        'https://api.nuxtjs.dev/posts'
      ).then(res => res.json())
    },
    name: "IndexPage",
    components: { Card }
}
</script>
