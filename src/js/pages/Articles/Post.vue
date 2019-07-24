<template lang="html">
  <app-article-post
    :article-title="'ダミータイトル'"
    :article-content="'ダミー本文ダミー本文ダミー本文ダミー本文ダミー本文ダミー本文'"
    :markdown-content="markdownContent"
    :category-list="[{ id: 1, name: 'ダミーカテゴリー' }]"
    :access="access"
  />
</template>

<script>
import { ArticlePost } from '@Components/molecules';

export default {
  components: {
    appArticlePost: ArticlePost,
  },
  computed: {
    markdownContent() {
      return '# ダミータイトル\nダミー本文ダミー本文ダミー本文ダミー本文ダミー本文ダミー本文';
    },
    access() {
      return this.$store.getters['auth/access'];
    },
  },
};
</script>

<style lang="postcss" scoped>
.article-edit {
  display: flex;
  height: 100%;
  &-editor {
    padding-right: 2%;
    width: 50%;
    border-right: 1px solid #ccc;
  }
  &-preview {
    margin-left: 2%;
    width: 48%;
    overflow-y: scroll;
    background-color: #fff;
  }
  &-form {
    margin-top: 20px;
  }
}
</style>
