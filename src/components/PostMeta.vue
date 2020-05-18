<template>
   <div class="post-meta">
      Posted {{ formattedDate(post.created_utc) }} ago on {{ post.domain }}
    </div>
</template>

<script>
import { formatDistance } from 'date-fns'

export default {
  props: ['post'],
  methods: {
    formattedDate(epoch) {
      return formatDistance(new Date(epoch * 1000), new Date())
    }
  }
}
</script>

<style lang="scss">
.post-meta {
  font-size: .8em;
  opacity: .8;
}
</style>
