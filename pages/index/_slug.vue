<template>
  <div>
    <div @show="flipIt()">
      <div
        class="
          bg-gray-900 bg-opacity-90
          h-screen
          w-screen
          fixed
          top-0
          left-0
          flex
          items-center
          justify-center
          layer
        "
      ></div>
      <div class="h-screen w-screen fixed top-0 left-0 flex justify-center">
        <div
          class="w-full bg-gray-800 rounded-xl overflow-scroll m-12 card"
          :data-flip-id="`card-` + post.id"
        >
          <n-link to="/">
            <img
              :src="post.image"
              alt
              class="w-full object-cover img"
              :data-flip-id="`img-` + post.id"
            />
            <h2 class="p-8 text-3xl text-white">{{ post.title }}</h2>
            <p class="p-8 text-gray-300">
              {{ post.description }}
            </p>
          </n-link>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  async asyncData({ $content, params }) {
    post = await $content("https://api.nuxtjs.dev/posts/" + params.slug).then((res) => res.json());

    return {
      post,
    };
  },
  // data() {
  //   return {
  //     post: [],
  //   };
  // },
  // async fetch() {
  //   this.post = await fetch(
  //     "https://api.nuxtjs.dev/posts/" + this.$route.params.slug
  //   ).then((res) => res.json())
    
  // },
  transition: {
    name: "test",
    mode: "out-in",
    // enter(el, done) {
    //   this.$nextTick(() => {
    //     const state = this.$Flip.getState(".card, .img");
    //     this.$Flip.from(state, {
    //       duration: 0.5,
    //       ease: "power3.inOut",
    //     });
    //   });
    // },
    leave(el, done) {
      this.$nextTick(() => {
        const state = this.$Flip.getState(".card, .img");
        this.$Flip.to(state, {
          duration: 0.5,
          ease: "power3.inOut",
          onComplete: done,
        });
      });
    },
  },
  methods: {
    flipIt() {
       console.log('hurz')
      this.$nextTick(() => {
        const state = this.$Flip.getState(".card, .img");
        console.log(state)
        this.$Flip.from(state, {
          duration: 0.5,
          ease: "power3.inOut",
        });
      });
    }
  },
  mounted () {
  },
};
</script>

<style>
/* .test-enter-active .layer {
  opacity: 0;
}
.test-leave-active .layer {
  opacity: 0;
} */
</style>