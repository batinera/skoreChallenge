<template>

  <div class="content">
    <div class="content-inner">
      <div class="content-text-wrap">
        <article v-for="content in contents" :key="content.id">
          <h1> {{ content.title }} </h1>
        </article>
      </div>
    </div>
  </div>

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

<style src="../assets/style/contents.css">

</style>