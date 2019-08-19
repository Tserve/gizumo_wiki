<template lang="html">
  <details>
    <summary
      class="accordion-heading"
      :class="{ 'open': isShow }"
      @click="toggleShow"
    >
      {{ title }}
    </summary>
    <transition name="fade">
      <div
        v-if="isShow"
        class="accordion-list"
      >
        <slot />
      </div>
    </transition>
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
  .accordion-heading {
    cursor: pointer;
    position: relative;
    user-select: none;
    padding: 10px;
  }
  .accordion-heading:after {
    position: absolute;
    top: 15px;
    right: 0;
    border: 5px solid transparent;
    width: 0;
    height: 0;
    content: "";
    border-top: 5px solid #666;
    transform: rotate(-90deg);
    transition: all .3s;
  }
  .open:after {
    transform: rotate(0deg);
  }
  .accordion-list {
    padding-left: 10px;
    padding-bottom: 10px;
  }
  .fade-enter-active, .fade-leave-active {
    transition: opacity .3s;
  }
  .fade-enter, .fade-leave-to {
    opacity: 0;
  }
</style>
