<template>
  <main>
    <div class="content">
    <article v-for="content in contents" :key="content.title" :content="content" class="article">
      <h1> {{ content.title }} </h1>
    </article>
  </div>
  </main>
</template>

<script>
import gql from 'graphql-tag'

const contents = gql`
  query contents {
    contents {
      id
      title
      description
      type
      url
      created_at
      updated_at
    }
  }
  `

export default {
  apollo: {
    contents: {
      query: contents,
      prefetch: true
    }
  }
}
</script>