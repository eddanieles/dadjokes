<template>
  <div class="joke">
    <p>
        <nuxt-link :to="`/jokes/${id}`">{{joke}}</nuxt-link> 
    </p>
  </div>
</template>

<script>
export default {
    name: "Joke",
    props: ["joke", "id"]
}
</script>

<style>
    .joke {
        padding: 1rem;
        border: 1px dotted black;
        margin: 1rem 0;
    }
</style>