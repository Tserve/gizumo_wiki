<template lang="html">
  <div>
    <app-heading :level="1">
      削除した記事
    </app-heading>
    <app-list-item
      v-for="article in targetArray"
      :key="article.id"
      list-style-none
      bg-white
      large
      border-bottom-gray
    >
      <app-accordion
      class="accordion"
        :title="article.title"
      >
        <li>
          作成日: {{ article.created_at }}
        </li>
        <li>
          作者: {{ article.user.full_name }}
        </li>
        <li>
          本文: {{ article.content }}
        </li>
      </app-accordion>
    </app-list-item>
  </div>
</template>

<script>
import {
  Heading,
  ListItem,
  Text,
  Accordion,
  Button,
} from '@Components/atoms';

export default {
  components: {
    appHeading: Heading,
    appListItem: ListItem,
    appText: Text,
    appAccordion: Accordion,
    appButton: Button,
  },
  props: {
    targetArray: {
      type: Array,
      default: () => [],
    },
  },
};
</script>
