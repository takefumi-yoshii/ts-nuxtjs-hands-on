<template>
  <div class="wrapper">
    <h1 class="title">
      {{title}}
    </h1>
    <AppArticle :article="article" />
  </div>
</template>

<script lang="ts">
import Vue from 'vue'
import { Context } from '@nuxt/vue-app'
import { ArticleData } from '../types/article'
import AppArticle from '../components/AppArticle.vue'

interface Data {
  title: string
}
interface AsyncData {
  article: {
    created_at: string
    title: string
    author: string
    body: string
  }
}
export default Vue.extend({
  components: {
    AppArticle
  },
  data(): Data {
    return { title: 'Nuxt x TypeScript' }
  },
  async asyncData({ query, $axios }: Context): Promise<AsyncData> {
    const { data } = await $axios.get<ArticleData>(
      `/api/v1/article/${query.page || 0}`
    )
    return { article: data.article }
  }
})
</script>

<style scoped>
.title {
  margin-bottom: 20px;
}
.wrapper {
  padding: 40px;
}
</style>
