<template>
  <transition @enter="maskEnter" @leave="maskLeave" :css="false">
    <div v-if="isActive" class="c-mask"></div>
  </transition>
</template>
<style lang="scss" scoped>
@import "../../../../assets/sass/theme/index";

.c-mask {
  pointer-events: none;
  position: fixed;
  opacity: 0;
  background: $primary-bg-s;
  border-radius: $radius;
  z-index: $gi-zindex-mask;
}
</style>
<script>
import mixinTransitions from './mixinTransitions.js'

export default {
  name: 'Masker',
  mixins: [ mixinTransitions ],
  props: {
    isActive: Boolean,
    elementsSize: Object
  }
}
</script>
