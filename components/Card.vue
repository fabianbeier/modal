<template>
    <div class="bg-gray-800 rounded-xl overflow-hidden card"  >
        <n-link to="/child1">
            <img
                src="https://picsum.photos/id/1015/1000/1000"
                alt
                class="w-full h-96 object-cover img" :data-flip-id="img"
            />
            <h2 class="p-8 text-3xl text-white">Hallo Welt</h2>
            <p
                class="p-8 text-gray-300"
            >Lorem ipsum dolor sit amet consectetur adipisicing elit. Doloribus numquam voluptas, iusto vitae dolorum dicta reiciendis ratione eaque excepturi quis debitis temporibus ab a nesciunt qui tempora quisquam, ullam cupiditate.</p>
        </n-link>
    </div>
</template>

<script>
export default {
   props: ['img']
}
</script>

<style>
</style>