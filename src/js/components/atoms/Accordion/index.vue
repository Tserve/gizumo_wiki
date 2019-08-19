<template lang="html">
  <details>
    <summary
      class="accordionHeading"
      @click="toggleShow"
    >
      {{ title }}
    </summary>
    <div
      v-if="isShow"
      :class="classes"
    >
      <slot />
    </div>
  </details>
</template>

<script>
export default {
  props: {
    accordionList: {
      type: Boolean,
      default: false,
    },
    title: {
      type: String,
      default: '',
    },
  },
  data() {
    return {
      isShow: false,
    };
  },
  computed: {
    classes() {
      return {
        'accordion-list': this.accordionList,
      };
    },
  },
  methods: {
    toggleShow() {
      this.isShow = !this.isShow;
    },
  },
};
</script>

<style lang="postcss" scoped>
  .accordionHeading{
    cursor: pointer;
  }
</style>
