<template>
  <div class="blog-post">
    <h3>{{ post.title }}</h3>
    <button v-on:click="$emit('enlarge-text',0.1)">Enlarge text</button>
    <button v-on:click="$emit('narrow-text',0.1)">narrow text</button>
  </div>
</template>

<script>
export default {
  name: "button-counter",
  props: ["post"],
  data(){
    return {

    }
  }
};
</script>

<style>
</style>