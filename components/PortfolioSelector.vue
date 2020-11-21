<template>
  <div class="portfolio-container">
    <div class="portfolio-selector1 background on"></div>
    <div class="portfolio-selector2 background off"></div>

    <div class="links">
      <h2>Portfolio</h2>

      <div>
        <a
          v-for="(opt, i) in options"
          :key="i"
          href="#"
          :class="'button button--' + opt.short + ' ' + isactive(i)"
          @click="fire(opt)"
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
    <div v-show="portfolioShow" class="portfolio-container2">
      {{ currentList() }}
      <PortfolioList :options="currentList()"></PortfolioList>
      <PortfolioDetails :options="currentList()"></PortfolioDetails>
    </div>
  </div>
</template>
<script>
export default {
  data() {
    return {
      image: '~assets/background.jpg',
      selectedKey: 'featured',
      portfolioShow: true,
      selectedOptions: [],
      options: [
        {
          icon: ['fas', 'star'],
          short: 'featured',
        },
        {
          icon: ['fas', 'clipboard-list'],
          short: 'wip',
        },
        {
          icon: ['fab', 'codepen'],
          short: 'codepen',
        },
        {
          icon: ['fas', 'bolt'],
          short: 'stackblitz',
        },
        {
          icon: ['fab', 'github-alt'],
          short: 'github',
        },
      ],
      portfolioList: {
        featured: [
          { name: 'Goodreads API Search' },
          { name: 'Google Books API Search' },
          { name: '' },
          { name: 'angular 1234 project' },
          { name: 'angular 1234 project' },
          { name: 'angular 1234 project' },
        ],
        wip: [],
        codepen: [],
        stackblitz: [],
        github: [],
      },
    }
  },
  computed: {},
  created() {
    // this.selectedOptions = this.portfolioList[this.selectedKey]
  },

  methods: {
    currentList() {
      const key = this.selectedKey
      return this.portfolioList[key]
    },
    isactive(i) {
      return i === 0 ? 'active' : 'non-active'
    },
    fire(opt) {
      this.updateSelected(opt.short)
    },
    updateSelected(key) {
      this.selectedKey = key
      this.selectedOptions = this.portfolioList[key]
    },
    showNum(i) {
      return i < 10 ? '0' + (i + 1) : i
    },
  },
}
</script>

<style lang="scss" scoped>
.background {
  position: fixed;
  width: 100%;
  height: calc(100vh - 125px);
  -webkit-filter: grayscale(0.75) blur(5px) brightness(50%);
  -moz-filter: grayscale(0.75) blur(5px) brightness(50%);
  -o-filter: grayscale(0.75) blur(5px) brightness(50%);
  -ms-filter: grayscale(0.75) blur(5px) brightness(50%);
  filter: grayscale(0.75) blur(5px) brightness(50%);
  -webkit-transition: all 0.5s linear;
  -moz-transition: all 0.5s linear;
  -o-transition: all 0.5s linear;
}
.off {
  opacity: 0;
}

.on {
  bottom: 1%;

  transition: all 0.5s linear;
}
.portfolio-selector1 {
  background-image: url('~assets/background2.jpg');
  background-size: cover;
}
.portfolio-selector2 {
  background-image: url('~assets/background.jpg');
  background-size: cover;
}
.links {
  position: relative;
  z-index: 2;
  width: 100%;
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
.portfolio-container {
  width: 100%;
  font-family: 'Heebo', sans-serif !important;
  display: flex;
  justify-content: center;
  flex-wrap: wrap;
}
.portfolio-container2 {
  display: flex;
  width: 50%;
  justify-content: center;
  padding: 1em;
  margin: 1em;
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

@include make-btn('featured', lighten(royalblue, 5%));

@include make-btn('wip', lighten(#3b8070, 10%));
@include make-btn('codepen', lighten(maroon, 30%));
@include make-btn('github', #eee, #222);
@include make-btn('stackblitz', darken(gold, 5%));
</style>
