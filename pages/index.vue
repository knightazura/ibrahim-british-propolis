<template>
  <div class="container bg-red-100">
    <div>
      <div class="bg-white rounded-lg p-6 shadow-lg mb-4">
        <div>
          <h2 class="text-lg">Erin Lindford</h2>
          <div class="text-purple-500">Product Engineer</div>
          <div clas>erinlindford@example.com</div>
          <div clas>(555) 765-4321</div>
        </div>
      </div>
      <li v-for="post of posts" :key="post.slug">
        <NuxtLink :to="'/blog/' + post.slug">{{ post.title }}</NuxtLink>
      </li>
    </div>
  </div>
</template>

<script lang="ts">
import Vue from 'vue'

export default Vue.extend({
  head() {
    return {
      script: [{ src: 'https://identity.netlify.com/v1/netlify-identity-widget.js' }],
    };
  },
  async asyncData({ $content }) {
    const posts = await $content("blog").fetch();

    return {
      posts,
    };
  },
})
</script>

<style>
.container {
  @apply min-h-screen flex justify-center items-center mx-auto;
}

.title {
  font-family:
    'Quicksand',
    'Source Sans Pro',
    -apple-system,
    BlinkMacSystemFont,
    'Segoe UI',
    Roboto,
    'Helvetica Neue',
    Arial,
    sans-serif;
  display: block;
  font-weight: 300;
  font-size: 100px;
  color: #35495e;
  letter-spacing: 1px;
}

.subtitle {
  font-weight: 300;
  font-size: 42px;
  color: #526488;
  word-spacing: 5px;
  padding-bottom: 15px;
}

.links {
  padding-top: 15px;
}
</style>
