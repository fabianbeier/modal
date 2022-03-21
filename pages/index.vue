<template>
  <div class="m-12">
    <ul class=" grid grid-cols-2 gap-5">
      <li><Card/></li>
      <li><Card/></li>
      <li><Card/></li>
      <li><Card/></li>
      <li><Card/></li>
      <li><Card/></li>
      <li><Card data-flip-id="card" img="img"/></li>
      <li><Card/></li>
      <li><Card/></li>
    </ul>
    <nuxt-child/>
  </div>
</template>

<script>
import Card from "~/components/Card.vue";
export default {
    name: "IndexPage",
    components: { Card }
}
</script>
