<template>
  <div v-if="showFallback" class="c-avatar" :class="{ [size]: size, hasMargin }" v-on="$listeners"
    :style="{ backgroundColor: fallbackBg }"
  />
  <img v-else :src="src" :alt="alt" class="c-avatar" :class="{ [size]: size, hasMargin }"
    @error="handleFallback"
    v-on="$listeners"
  />
</template>
<style lang="scss" scoped>
@import "../../assets/sass/theme/index";

@mixin size($value) {
  width: $value;
  max-width: $value;
  height: $value;
  max-height: $value;
  background-color: $body-background-color;
}

.c-avatar {
  border-radius: 50%;

  &.hasMargin {
    margin-right: $gi-spacer-sm;
  }

  &.xs { @include size($gi-spacer); }

  &.sm { @include size($gi-spacer*1.5); }

  &.md { @include size($gi-spacer*2); }

  &.lg { @include size($gi-spacer*3); }

  &.xl { @include size($gi-spacer*4); }
}
</style>
<script>
export default {
  name: 'Avatar',
  props: {
    src: String,
    alt: {
      type: String,
      default: ''
    },
    size: {
      type: String,
      default: 'md',
      validator (value) {
        return ['xs', 'sm', 'md', 'lg', 'xl'].indexOf(value) !== -1
      }
    },
    fallbackBg: String,
    /** When true a right margin is added - useful when there's text on the side */
    hasMargin: Boolean
  },
  data () {
    return {
      showFallback: false
    }
  },
  methods: {
    handleFallback () {
      this.showFallback = true
    }
  }
}
</script>
