<template>
  <NuxtLink
    :to="{
      path: 'detailsPortfolio',
      query: { category: cat, project: index },
    }"
    :style="{ background: option.links.color || '#000' }"
    class="button button--lite"
  >
    <slot></slot>
  </NuxtLink>
</template>
<script>
export default {
  props: {
    option: {
      type: Object,
      default() {
        return {}
      },
    },
    index: {
      type: Number,
      default() {
        return 0
      },
    },
    cat: {
      type: String,
      default() {
        return ''
      },
    },
  },
}
</script>

<style lang="scss" scoped>
.button {
  position: relative;
  z-index: 2;
  display: inline-flex;
  justify-content: space-between;
  align-content: center;
  align-items: center;
  text-align: center;
  // border-radius: 4px;
  text-decoration: none;
  text-transform: capitalize;
  color: white;
  border-radius: 5px;
  margin-bottom: 1em;
  font-family: 'Heebo', sans-serif !important;
  font-size: 12px;
  -webkit-font-smoothing: antialiased;
  font-weight: 600;
  padding: 1em;
}
@mixin make-btn($name, $color, $textColor: rgba(0, 0, 0, 0.4)) {
  .button--#{$name} {
    color: white;
    text-shadow: 2px 2px 8px rgba(0, 0, 0, 0.8);
    // background: red;
    svg {
      color: transparent !important;
    }
    &:active {
      position: relative;
      top: 1px;
      left: 1px;
    }
    &[disabled] {
      background: lighten($color, 30%);
      border-color: lighten($color, 30%);
      color: black;
      text-shadow: none;
    }
  }
}

@include make-btn('lite', white);
</style>
