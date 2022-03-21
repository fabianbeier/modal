<template>
    <div class="">
        <div class="bg-gray-900 bg-opacity-90 h-screen w-screen fixed top-0 left-0 flex items-center justify-center layer"></div>
        <div
            class="h-screen w-screen fixed top-0 left-0 flex items-center justify-center"
        >
            <div class="w-1/2 bg-gray-800 rounded-xl overflow-hidden card" data-flip-id="card">
                <n-link to="/">
                    <img
                        src="http://fakeimg.pl/500x500?font=bebas"
                        alt
                        class="w-full h-96 object-cover"
                    />
                    <h2 class="p-8 text-3xl text-white">Jetzt ein anderer Titel</h2>
                    <p
                        class="p-8 text-gray-300"
                    >Lorem ipsum dolor sit amet consectetur adipisicing elit. Doloribus numquam voluptas, iusto vitae dolorum dicta reiciendis ratione eaque excepturi quis debitis temporibus ab a nesciunt qui tempora quisquam, ullam cupiditate.</p>
                </n-link>
            </div>
        
        </div>
    </div>
</template>

<script>
export default {
    transition: {
        name: 'test',
        mode: '',
        css: false,

        enter(el, done) {
            this.$nextTick(() => {
            const state = this.$Flip.getState('.card, .parent')
            
                this.$Flip.from(state, {
                    duration: 1,
                    ease: "power1.inOut",
                    scale: true,
                    nested: true,
                    onComplete: 
                             this.$gsap.from('.layer', {
                        opacity: 0,
                        duration: 1,
                    ease: "power1.inOut",

                    }
                    )

                   
                })
            })
        },
        leave(el, done) {
            this.$nextTick(() => {
            const state = this.$Flip.getState('.card, .parent')
            
                this.$Flip.to(state, {
                    duration: 1,
                    scale: true,
                    nested: true,
                    ease: "power1.inOut",
                    onComplete: done,
                })
            })
        },
    }
}
</script>

<style>
</style>