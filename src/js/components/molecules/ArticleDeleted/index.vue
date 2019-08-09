<template lang="html">
  <div>
    <app-heading :level="1">
      削除した記事
    </app-heading>
    <app-list-item>
      <app-text>
        {{  }}
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
}
</script>

<style lang="postcss" scoped>

</style>
