<template lang="html">
  <div class="articles">
    <app-article-list
      :title="title"
      :target-array="[{
        'id': 82,
        'user': {
          'id': 4,
          'account_name': 'komatti',
          'full_name': '小松 信之',
          'email': 'komatti@test.com',
          'role': {
            'id': 1,
            'name': 'システム管理者',
            'value': 'system'
          },
          'password_reset_flg': 1,
          'created_at': '2019-07-01T09:54:36.000000Z',
          'updated_at': '2019-07-09T11:44:45.000000Z'
        },
        'title': 'タイトルのテスト3',
        'content': 'テスト本文テスト本文テスト本文テスト本文テスト本文テスト本文テスト本文テスト本文テスト本文テスト本文テスト本文テスト本文テスト本文',
        'category': {
          'id': 1,
          'name': '全体'
        },
        'created_at': '2019-07-16T09:32:46.000000Z',
        'updated_at': '2019-07-16T09:32:46.000000Z'
      }]"
      :access="access"
      @openModal="openModal"
    />
  </div>
</template>

<script>
import { ArticleList } from '@Components/molecules';
import Mixins from '@Helpers/mixins';

export default {
  components: {
    appArticleList: ArticleList,
  },
  mixins: [Mixins],
  beforeRouteUpdate(to, from, next) {
    this.fetchArticles();
    next();
  },
  data() {
    return {
      title: 'すべて',
    };
  },
  computed: {
    articlesList() {
      return this.$store.state.articles.articleList;
    },
    access() {
      return this.$store.getters['auth/access'];
    },
  },
  methods: {
    openModal() {
      this.toggleModal();
    },
  },
};
</script>
