<template>
  <Layout :show-logo="false">
    <Author :show-title="true" />
    <div class="posts">
      <div
        v-if="posts.length === 0"
        class="loading"
      >
        Loading...
      </div>
      <PostCard
        v-for="post in posts"
        :key="post.id"
        :post="post"
      />
    </div>

  </Layout>
</template>

<script>
import Author from '~/components/Author.vue'
import PostCard from '~/components/PostCard.vue'

export default {
  components: {
    Author,
    PostCard
  },
  data: () => ({
    posts: []
  }),
  mounted() {
    fetch('https://api.pushshift.io/reddit/search/submission/?subreddit=bigtech')
      .then(response => {
        return response.json()
      })
      .then(json => {
        this.posts = json.data
      });
  }
}
</script>

<style scoped>
.loading {
  display: flex;
  align-items: center;
  justify-content: center;
}
</style>
