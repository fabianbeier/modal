<template>
  <div class="m-12" >
    <ul class="grid grid-cols-3 gap-8">
      <li v-for="post in posts" :key="post.id"><Card :content="post" /></li>
    </ul>
    <nuxt-child />
  </div>
</template>

<script>
import Card from "~/components/Card.vue";
export default {
  data() {
    return {
      posts: [],
    };
  },
  async fetch() {
    this.posts = await fetch("https://api.nuxtjs.dev/posts").then((res) =>
      res.json()
    );
  },
  name: "IndexPage",
  components: { Card },
  transition: {
    name: 'startpage',
    mode: "out-in",
    appear: true,
    enter(el, done) {
      this.$gsap.from('.card', {
        y: 100,
        opacity: 0,
        duration: 0.5,
        stagger: 0.05
      })
    }
  },
  methods: {
    pathTest() {
      // history.pushState({}, '', "asdh")
    },
  },
};
</script>
