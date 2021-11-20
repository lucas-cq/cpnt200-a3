<template>
  <div>
  <GlobalNav />
    <section>
      <h2>{{ post.title }}</h2>
      <nuxt-img :src="post.image" width="400"/>
      <p>Date Added: {{ post.date }} robot time</p>
    </section>
  <MyFooter />
  </div>
</template>

<style scoped>

</style>

<script>
export default {
  async asyncData({ $content, params, error }) {
    try {
      const post = await $content(`gallery/${params.slug}`).fetch()
      return {
        post,
      }
    } catch (error) {
      error('Gallery Not found')
    }
  }
}
</script>