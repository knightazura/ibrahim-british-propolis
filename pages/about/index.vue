<template>
  <div>
    <h1>THIS SHOULD BE</h1>
    <h2>{{ page.title }}</h2>
    <p>{{ page.description }}</p>
  </div>
</template>

<script>
export default {
  async asyncData({ $content, params, error }) {
    let page;
    try {
      page = await $content("pages/about-page").fetch();
    } catch (e) {
      error({ message: "Page not found" });
    }

    return {
      page,
    };
  },
};
</script>