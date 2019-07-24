<template lang="html">
  <app-article-edit
    :access="access"
    :article-title="'ダミータイトル'"
    :article-content="'ダミー本文ダミー本文ダミー本文ダミー本文ダミー本文ダミー本文'"
    :markdown-content="markdownContent"
    :current-category-name="'ダミーカテゴリー'"
    :category-list="[{ id: 1, name: 'ダミーカテゴリー' }]"
  />
</template>

<script>
import { ArticleEdit } from '@Components/molecules';

export default {
  components: {
    appArticleEdit: ArticleEdit,
  },
  computed: {
    access() {
      return this.$store.getters['auth/access'];
    },
    markdownContent() {
      return '# ダミータイトル\nダミー本文ダミー本文ダミー本文ダミー本文ダミー本文ダミー本文';
    },
    currentCategoryName() {
      return 'ダミーカテゴリー';
    },
  },
};
</script>
