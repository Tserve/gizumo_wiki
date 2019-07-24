<template lang="html">
  <form @submit.prevent="addCategory">
    <app-heading :level="1">カテゴリー管理</app-heading>
    <app-input
      v-validate="'required'"
      name="category"
      type="text"
      placeholder="追加するカテゴリー名を入力してください"
      data-vv-as="カテゴリー名"
      :error-messages="errors.collect('category')"
    />
    <app-button
      class="category-management-post__submit"
      button-type="submit"
      round
    >
      {{ buttonText }}
    </app-button>

    <div class="category-management-post__notice">
      <app-text bg-error>ここにエラー時のメッセージが入ります</app-text>
    </div>

    <div class="category-management-post__notice">
      <app-text bg-success>ここに作成成功時のメッセージが入ります</app-text>
    </div>
  </form>
</template>
<script>
import {
  Heading, Input, Button, Text,
} from '@Components/atoms';

export default {
  components: {
    appHeading: Heading,
    appInput: Input,
    appButton: Button,
    appText: Text,
  },
  props: {
    access: {
      type: Object,
      default: () => ({}),
    },
  },
  computed: {
    buttonText() {
      if (!this.access.create) return '作成権限がありません';
      return '作成';
    },
  },
  methods: {
    addCategory() {
      if (!this.access.create) return;
      this.$validator.validate().then((valid) => {
        if (valid) this.$emit('handleSubmit');
      });
    },
  },
};
</script>
<style lang="postcss" scoped>
.category-management-post {
  &__input {
    margin-top: 16px;
  }
  &__submit {
    margin-top: 16px;
  }
  &__notice {
    margin-top: 16px;
  }
}
</style>
