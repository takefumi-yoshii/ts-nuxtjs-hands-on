<template>
  <div class="container">
    <h2>
      {{article.title}}
    </h2>
    <div v-html="article.body" />
  </div>
</template>

<script lang="ts">
import Vue from 'vue'
import { ArticleData } from '../types/article'

export default Vue.extend({
  props: {
    article: Object as () => ArticleData
  }
})
</script>

<style scoped>
h2 {
  margin-bottom: 12px;
  font-size: 24px;
}
.container {
  padding: 20px;
  border: 2px solid #000;
  border-radius: 10px;
}
</style>
