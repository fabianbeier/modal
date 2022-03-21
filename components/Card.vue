<template>
    <div class="bg-gray-800 rounded-xl overflow-hidden card" :data-flip-id="`card-`+content.id" >
        <n-link :to="content.slug">
            <img
                :src="content.image"
                alt
                class="w-full h-96 object-cover img" :data-flip-id="`img-`+content.id"
            />
            <h2 class="p-8 text-3xl text-white">{{content.title}}</h2>
            <p
                class="p-8 text-gray-300"
            >{{content.description}}</p>
        </n-link>
    </div>
</template>

<script>
export default {
   props: ['img', 'content']
}
</script>

<style>
</style>