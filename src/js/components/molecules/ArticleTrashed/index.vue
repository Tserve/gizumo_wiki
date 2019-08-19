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
      border-bottom-gray
    >
      <app-accordion
        class="accordion"
        :title="article.title"
      >
        <li>
          作成日: {{ replacedTime }}
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
  Accordion,
} from '@Components/atoms';

export default {
  components: {
    appHeading: Heading,
    appListItem: ListItem,
    appAccordion: Accordion,
  },
  props: {
    targetArray: {
      type: Array,
      default: () => [],
    },
  },
  computed: {
    replacedTime() {
      let replacedTime = '';
      for (let i = 0; i < this.targetArray.length; i += 1) {
        replacedTime = this.targetArray[i].created_at
          .replace(/-/g, '/').substr(0, 10);
      }
      return replacedTime;
    },
  },
};
</script>
