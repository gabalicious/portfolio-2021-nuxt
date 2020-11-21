<template>
  <a href="#" class="button button--lite"> <slot></slot> <Arrow /></a>
</template>
<script>
export default {
  props: {
    options: {
      type: Array,
      default() {
        return []
      },
    },
  },
  data() {
    return {}
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
  padding-left: 1.2em;
  padding-right: 1.2em;
  // border-radius: 4px;
  text-decoration: none;
  text-transform: capitalize;
  border: 1px solid #919191;
  color: white;
  width: 270px;
  height: 60px;
  margin-right: 1.5em;
  margin-bottom: 1em;
  font-family: 'Heebo', sans-serif !important;
  font-size: 12px;
  -webkit-font-smoothing: antialiased;
  font-weight: 600;
}
@mixin make-btn($name, $color, $textColor: white) {
  .button--#{$name} {
    color: white;
    text-shadow: 1px 1px 2px rgba(200, 200, 200, 0.2);
    svg {
      color: transparent !important;
    }
    &.active {
      color: rgb(216, 61, 29) !important;
      text-shadow: 1px 1px 3px rgba(50, 50, 50, 1);

      //   border-color: rgb(216, 61, 29);
      //   box-shadow: 1px 1px 5px rgba(200, 200, 200, 0.5);

      svg {
        color: rgb(216, 61, 29) !important;
      }
    }
    // &:hover {
    //   color: rgb(216, 61, 29);
    //   svg {
    //     color: rgb(216, 61, 29) !important;
    //   }
    // }
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
