<template>
  <div >
    <div >
      </div>
      <div class="h-screen w-screen fixed top-0 left-0 flex justify-center bg-slate-900 transition-all duration-150 layer bg-opacity-90">
        <div
          class="w-full bg-gray-200 rounded-xl overflow-scroll m-12 card"
          :data-flip-id="`card-` + post.id"
        >
          <n-link to="/">
            <img
              :src="post.image"
              alt
              class="w-full h-2/3 object-cover img"
              :data-flip-id="`img-` + post.id"
            />
            <div class="p-8">
                <h2 class="text-4xl pb-3">{{post.title}}</h2>
                <p class=" opacity-40 w-1/4 test" :data-flip-id="`text-` + post.id"
                >{{post.description}}</p>
            </div>
          </n-link>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  async asyncData({ $axios, params }) {
    const post = await $axios.$get(
      "https://api.nuxtjs.dev/posts/" + params.slug
    );

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
    mode: "in-out",
    afterEnter(el, done) {
      console.log("hurz");
      this.$nextTick(() => {
        const state = this.$Flip.getState(".card, .img, .test");
        this.$Flip.from(state, {
          duration: 0.5,
          ease: "power3.inOut",
          onComplete: done,
        });
      });
    },

    leave(el, done) {
      this.$nextTick(() => {
        const state = this.$Flip.getState(".card, .img, .test");
        this.$Flip.to(state, {
          duration: 0.5,
          ease: "power3.inOut",
          onComplete: done,
        });
      });
    },
  },

  mounted() {},
};
</script>

<style>
.test-enter-active .layer {
  opacity: 0;
}
.test-leave-active .layer {
  @apply bg-opacity-0;
}
</style>