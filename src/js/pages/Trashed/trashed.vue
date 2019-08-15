<template lang="html">
  <div>
    <app-article-trashed
      :target-array="trashedList"
    />
  </div>
</template>

<script>
import { ArticleTrashed } from '@Components/molecules';

export default {
  components: {
    appArticleTrashed: ArticleTrashed,
  },
  computed: {
    trashedList() {
      return this.$store.state.articles.trashedList;
    },
  },
  created() {
    this.getArticles();
  },
  methods: {
    getArticles() {
      this.$store.dispatch('articles/getTrashedList');
    },
  },
};
</script>
