<template>
  <div class="portfolio-container-top">
    <div>
      <div class="links">
        <h2>Portfolio</h2>

        <div v-if="options.items.length > 0">
          <a
            v-for="(opt, i) in options.items"
            :key="i"
            href="#"
            :class="'button button--' + opt.short + ' ' + isactive(opt.short)"
            @click="updateSelected(opt.short)"
          >
            <span class="num"> {{ showNum(i) }}. </span>
            <span class="short">{{ opt.short }}</span>
            <font-awesome-icon
              :style="{ color: 'inherit', paddingLeft: '2px' }"
              :icon="opt.icon"
            />
          </a>
        </div>
      </div>
      <div
        v-if="options.items.length > 0 && currentList()"
        class="portfolio-container-bottom"
      >
        <PortfolioList
          :cat="currentKey"
          :current="currentList()"
        ></PortfolioList>
      </div>
    </div>
  </div>
</template>
<script>
export default {
  async fetch() {
    this.portfolioArray = await fetch(
      'http://0.0.0.0:3000/_content/content'
    ).then((res) => res.json())
    this.options = await fetch(
      'http://0.0.0.0:3000/_content/options'
    ).then((res) => res.json())
    /* eslint-disable */
    console.log('Async fetch call')
  },

  data() {
    return {
      image: '~assets/background.jpg',
      selectedKey: 'frontend',
      selectedPortfolio: 0,
      portfolioShow: true,
      selectedOptions: [],
      options: { items: [] },
      portfolioArray: {},
    }
  },
  computed: {},
  created() {
    // this.selectedOptions = this.portfolioArray[this.selectedKey]
  },

  methods: {
    currentList() {
      const key = this.selectedKey

      return this.portfolioArray[key].items
    },
    currentKey() {
      return this.selectedKey
    },

    isactive(i) {
      return i === this.selectedKey ? 'active' : 'non-active'
    },

    updateSelected(key) {
      // console.log('Updating key: ', key)
      this.selectedKey = key
      return this.selectedKey
    },

    showNum(i) {
      return i < 10 ? '0' + (i + 1) : i
    },
  },
}
</script>

<style lang="scss" scoped>
.links {
  position: relative;
  z-index: 2;
  width: 100%;
  text-align: center;
  h2 {
    color: white;
  }
}
.short {
  padding: 0 0.5em;
  text-transform: uppercase;
  font-size: 14px;
  font-weight: 400;
}
.num {
  font-size: 13px;
  font-weight: 400;
}
.portfolio-container-top {
  width: 100%;
  font-family: 'Heebo', sans-serif !important;
  display: flex;
  justify-content: center;
  flex-wrap: wrap;
  background: transparent;
}
.portfolio-container-bottom {
  display: flex;
  // justify-content: center;
  padding: 1em 0;
  margin: 1em 0;
  position: relative;
  z-index: 1;
}

.button {
  display: inline-block;
  // border-radius: 4px;
  text-decoration: none;
  padding: 10px 10px;
  border: 3px transparent solid;
  font-size: 16px;
  text-transform: capitalize;
  flex-basis: calc(100%);
  width: calc(100%);
  @media (min-width: 500px) {
    flex-basis: calc(50% - 26px);
    width: calc(50% - 26px);
  }
  @media (min-width: 900px) {
    width: unset;
    flex-basis: unset;
  }
}
.button + .button {
  margin-left: 15px;
}

@mixin make-btn($name, $color, $textColor: white) {
  .button--#{$name} {
    color: white;
    text-shadow: 1px 1px 5px rgba(50, 50, 50, 0.6);
    &.active {
      border-bottom: 3px $color solid;
    }
    &:hover {
      border-bottom: 3px $color solid;
    }
    &:active {
      position: relative;
      top: 1px;
      left: 1px;

      border-bottom: 3px $color solid;
    }
    &[disabled] {
      background: lighten($color, 30%);
      border-color: lighten($color, 30%);
      color: black;
      text-shadow: none;
    }
  }
}

@include make-btn('frontend', lighten(royalblue, 5%));

@include make-btn('github', lighten(#3b8070, 10%));
@include make-btn('experiments', lighten(maroon, 30%));
@include make-btn('fullstack', darken(#f0ca00, 3%), #222);
// @include make-btn('stackblitz', darken(gold, 5%));
</style>
