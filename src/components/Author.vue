<template>
  <div class="author">

    <h1 v-if="showTitle" class="author__site-title">
      {{ $static.metadata.siteName }}
    </h1>

    <p class="author__intro">
      Following Big Tech's actions, relationship with governments and impact on society.
    </p>

  </div>
</template>

<static-query>
query {
  metadata {
    siteName
  }
}
</static-query>

<script>
export default {
  props: ['showTitle']
}
</script>

<style lang="scss">
.author {
  margin: 0 auto;
  max-width: 500px;
  text-align: center;
  padding-bottom: calc(var(--space) / 2);

  &__image {
    border-radius: 100%;
    width: 90px;
    height: 90px;
    margin-bottom: 1em;
  }

  &__intro {
    margin-top: 1em;
    opacity: .8;
    font-size: .8em;
  }

  &__site-title {
    margin: 0 auto;
    font-size: 1.5em;
    max-width: 400px;
  }

  &__links {
    margin-top: -.5em;
    a {
      margin: 0 .5em;
    }
  }
}
</style>
