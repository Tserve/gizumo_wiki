<template lang="html">
  <div>
    <app-heading :level="1">
      削除した記事
    </app-heading>
    <app-list-item
      v-for="article in targetArray"
      :key="article.id"
      flex
      beetween
      align-items
      bg-white
      large
      border-bottom-gray
    >
      <app-text>
        {{ article.title }}
      </app-text>
    </app-list-item>
  </div>
</template>

<script>
import {
  Heading,
  ListItem,
  Text,
} from '@Components/atoms';

export default {
  components: {
    appHeading: Heading,
    appListItem: ListItem,
    appText: Text,
  },
  props: {
    targetArray: {
      type: Array,
      default: () => [],
    },
  },
};
</script>

<style lang="postcss" scoped>

</style>
