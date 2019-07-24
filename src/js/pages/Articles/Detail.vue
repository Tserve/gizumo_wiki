<template lang="html">
  <app-article-detail
    :access="access"
    :markdown-indexes="markdownIndexes"
    :markdown-content="markdownContent"
    @parsedMarkdown="initIndex"
    @openModal="openModal"
    @handleClick="handleClick"
  />
</template>

<script>
import { ArticleDetail } from '@Components/molecules';
import Mixins from '@Helpers/mixins';

export default {
  components: {
    appArticleDetail: ArticleDetail,
  },
  mixins: [Mixins],
  data() {
    return {
      markdownIndexes: [],
    };
  },
  computed: {
    access() {
      return this.$store.getters['auth/access'];
    },
    markdownContent() {
      return '# ダミータイトル\nダミー本文ダミー本文ダミー本文ダミー本文ダミー本文ダミー本文';
    },
  },
  methods: {
    initIndex() {
      /**
       * TODO: マークダウンのhtmlがパースされた後にcreateMarkdownIndexesAnchorInfoメソッドを
       * 実行する必要があり、下記のsetTimeOutの処理だとパースした後を完全に保証しているわけではなく不完全なので、
       * 要修正
       */
      return new Promise((resolve) => {
        setTimeout(() => {
          this.createMarkdownIndexesAnchorInfo();
          resolve();
        }, 500);
      });
    },
    createMarkdownIndexesAnchorInfo() {
      const markdownIndexes = [];
      const markdownHtml = document.querySelector('.article-detail__markdown');
      if (markdownHtml) {
        const header = document.querySelector('header');
        const headerHeight = header.clientHeight;
        const hElements = markdownHtml.querySelectorAll('h1, h2');
        hElements.forEach((element, index) => {
          const tagName = element.tagName.toLowerCase();
          element.setAttribute('id', `${tagName}-${index}`);
          const idVal = element.getAttribute('id');
          const title = element.textContent;
          const { offsetTop } = element;
          const scrollToY = offsetTop - headerHeight;
          markdownIndexes.push({
            tagName,
            val: idVal,
            title,
            scrollToY,
          });
        });
        this.markdownIndexes = [...markdownIndexes];
        if (this.$route.hash) {
          this.smoothScroll();
        }
      }
    },
    smoothScroll() {
      const { hash } = this.$route;
      const anchorVal = hash.replace('#', '');
      const target = this.markdownIndexes.find(obj => anchorVal === obj.val);
      if (target) {
        this.$SmoothScroll(target.scrollToY);
      }
    },
    openModal() {
      this.toggleModal();
    },
    handleClick() {
      this.toggleModal();
    },
  },
};
</script>
