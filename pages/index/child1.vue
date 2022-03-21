<template>
  <div class="">
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
        transition-all 
      "
    ></div>
    <div
      class="
        h-screen
        w-screen
        fixed
        top-0
        left-0
        flex
        justify-center
      "
    >
      <div
        class="w-full bg-gray-800 rounded-xl overflow-scroll m-24 card"
        data-flip-id="card"
      >
        <n-link to="/">
          <img
            src="https://picsum.photos/id/1015/1000/1000"
            alt
            class="w-full  object-cover img" data-flip-id="img"
          />
          <h2 class="p-8 text-3xl text-white">Hallo Welt</h2>
          <p class="p-8 text-gray-300">
            Lorem ipsum dolor sit amet consectetur adipisicing elit. Doloribus
            numquam voluptas, iusto vitae dolorum dicta reiciendis ratione eaque
            excepturi quis debitis temporibus ab a nesciunt qui tempora
            quisquam, ullam cupiditate.
          </p>
        </n-link>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  transition: {
    name: "test",
    mode: "out-in",
    enter(el, done) {
      this.$gsap.to('body', {
          overflow: 'hidden'
      })  
      this.$nextTick(() => {
        const state = this.$Flip.getState(".card, .img");
        this.$Flip.from(state, {
        delay: 0.2,
          duration: 0.5,
          ease: "power3.inOut",
          onComplete: done,
        });
      });
      
    },
    leave(el, done) {
    this.$gsap.to('body', {
          overflow: 'scroll'
      }) 
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
};
</script>

<style>
.test-enter-active .layer{
    opacity: 0;
}
.test-leave-active .layer{
    opacity: 0;
}
</style>