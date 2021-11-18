<template>
  <article>
    <h2>{{ post.title }}</h2>
    <nuxt-content :document="post" />
  </article>
</template>

<script>
  export default {
  async asyncData({ $content, params, error }) {
    try {
      const post = await $content(`articles/${params.slug}`).fetch()
    } catch (error) {
      error({ message: "Post Not Found" })}
    },
    return: {
      article,
    },
  }
</script>
