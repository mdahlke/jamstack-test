<template>
  <main class="post individual" v-if="post">
    <router-link :to
    <h1>{{ post.title.rendered }}</h1>
    <section v-html="post.content.rendered"></section>
  </main>
</template>

<script>
  export default {
    data () {
      return {
        slug: this.$route.params.slug
      }
    },
    computed: {
      posts () {
        return this.$store.state.posts
      },
      post () {
        if (this.posts) {

          const p = this.posts.find(el => el.slug === this.slug)
          console.log(this.posts)
          return p
        }
        return {}
      }
    },
    created () {
      this.$store.dispatch('getPosts')
    }
  }
</script>

<style scoped>

</style>
