<template>
  <div :class="classObj" class="app-wrapper">
    <div class="main-container">
      <div class="fixed-header">
        <navbar />
      </div>
      <app-main />
    </div>
  </div>
</template>

<script>
import { Navbar, AppMain } from './components'
import ResizeMixin from './mixin/ResizeHandler'

export default {
  name: 'Layout',
  components: {
    Navbar,
    AppMain
  },
  mixins: [ResizeMixin],
  computed: {
    device() {
      return this.$store.state.app.device
    },
    fixedHeader() {
      return this.$store.state.settings.fixedHeader
    },
    classObj() {
      return {
        mobile: this.device === 'mobile'
      }
    }
  },
  methods: {
  }
}
</script>

<style lang="scss" scoped>
  @import "~@/styles/mixin.scss";
  @import "~@/styles/variables.scss";

  .app-wrapper {
    @include clearfix;
    position: relative;
    height: 100vh;
    width: 100%;
    &.mobile{
      position: fixed;
      top: 0;
    }
  }
  .fixed-header {
    position: relative;
    top: 0;
    right: 0;
    z-index: 9;
    width: 100%;
    transition: width 0.28s;
  }
</style>
