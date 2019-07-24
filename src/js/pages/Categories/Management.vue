<template lang="html">
  <div class="category-management">
    <section class="category-management-post">
      <app-category-post
        :access="access"
      />
    </section>
    <section class="category-management-list">
      <app-category-list
        :access="access"
        :theads="theads"
        :categories="[{ id: 1, name: 'ダミーカテゴリー' }]"
        @openModal="openModal"
      />
    </section>
  </div>
</template>

<script>
import { CategoryPost, CategoryList } from '@Components/molecules';
import Mixins from '@Helpers/mixins';

export default {
  components: {
    appCategoryPost: CategoryPost,
    appCategoryList: CategoryList,
  },
  mixins: [Mixins],
  data() {
    return {
      theads: ['カテゴリー名', '', '', ''],
    };
  },
  computed: {
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

<style lang="postcss" scoped>
.category-management {
  display: flex;
  height: calc(100vh - 94px);
  &-post {
    padding-right: 2%;
    width: 38%;
    border-right: 1px solid #ccc;
  }
  &-list {
    margin-left: 2%;
    width: 60%;
  }
}
</style>
