<template>
  <div class="product-layout">
    <mobile-layout v-if="mobile"></mobile-layout>
    <desktop-layout v-else></desktop-layout>
  </div>
</template>

<script>
import MobileDetect from 'mobile-detect';
import MobileLayout from 'components/Layout/MobileLayout';
import DesktopLayout from 'components/Layout/DesktopLayout';

export default {
  components: {
    MobileLayout,
    DesktopLayout
  },

  data() {
    return {
      mobile: false
    }
  },

  methods: {
    isMobile() {
      const md = new MobileDetect(window.navigator.userAgent);

      if(md.mobile()) {
        this.mobile = true;
      }
    }
  },

  mounted() {
    this.isMobile();
  }
}
</script>

<style lang="scss">
.product-layout {
  font-family: Arial, Helvetica, sans-serif;
}

p {
  margin: 0;
}
</style>
