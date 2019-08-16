<template lang="html">
  <div>
    <p
      style="cursor: pointer"
      @click="toggleShow"
    >
      {{ title }}
    </p>
    <div
      :class="classes"
      v-if="isShow"
    >
      <slot />
    </div>
  </div>
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
    }
  },
  data() {
    return {
      isShow: false,
    }
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
    }
  }
};
</script>
