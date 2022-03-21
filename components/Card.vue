<template>
    <div class="bg-gray-200 rounded-xl overflow-hidden card" :data-flip-id="`card-`+content.id" >
        <n-link :to="content.slug">
            <img
                :src="content.image"
                alt
                class="w-full h-96 object-cover img" :data-flip-id="`img-`+content.id"
            />
            <div class="p-8">
                <h2 class="text-4xl pb-3">{{content.title}}</h2>
                <p
                    class=" opacity-40 test" :data-flip-id="`text-` + content.id"
                >{{content.description}}</p>
            </div>
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