<template>
  <div class="portfolio-details">
    <NuxtLink class="back-link" to="/"
      ><BackArrow></BackArrow>Back to Portfolio</NuxtLink
    >
    <div
      v-if="query.category && portfolioArray[query.category]"
      class="container-content"
    >
      <div class="container-a">
        <div>
          <h2>
            {{ portfolioArray[query.category]['items'][query.project]['name'] }}
          </h2>
          <div></div>

          <p>
            {{
              portfolioArray[query.category]['items'][query.project][
                'description'
              ]
            }}
          </p>
        </div>

        <div class="link-container">
          <a
            :href="
              portfolioArray[query.category]['items'][query.project]['links']
                .code
            "
            target="_blank"
            rel="noopener noreferrer"
            class="button"
            :style="{
              background:
                portfolioArray[query.category]['items'][query.project].links
                  .color,
            }"
          >
            <font-awesome-icon
              :style="{ color: 'inherit' }"
              :icon="['fab', 'github-alt']"
            />
            <label for="">Browse Code</label>
          </a>
          <a
            :href="
              portfolioArray[query.category]['items'][query.project]['links']
                .demo
            "
            target="_blank"
            rel="noopener noreferrer"
            class="button"
            :style="{
              background:
                portfolioArray[query.category]['items'][query.project].links
                  .color,
            }"
          >
            <font-awesome-icon
              :style="{ color: 'inherit' }"
              :icon="['fas', 'external-link-alt']"
            />
            <label for="">Preview Demo</label>
          </a>
        </div>
      </div>
      <div class="container-b">
        <img
          :src="`/projects/${
            portfolioArray[query.category]['items'][query.project].image
          }`"
          alt=""
        />
      </div>
    </div>
  </div>
</template>
<script>
// eslint-disable-next-line

export default {
  watchQuery: true,

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
  // mounted() {
  //   this.testing = this.$hello(this)
  // },
  // asyncData({ app, $hello }) {
  //   this.$hello('params')

  //   $hello('params')
  // },

  data() {
    return {
      portfolioArray: {},
      testing: '',
    }
  },

  props: {
    query: {
      type: Object,
      default() {
        return {}
      },
    },
  },
}
</script>

<style lang="scss" scoped>
.button {
  height: 3.25rem;
  padding: 1rem;
  border-radius: 10px;
  color: white;
  box-shadow: 1px 1px 10px rgba(0, 0, 0, 0.5);
  display: inline-flex;
  align-items: center;
  width: 100%;
  margin: 1em 1em 1em auto;
  label {
    padding-left: 0.25rem;
  }
  @media (min-width: 1700px) {
    width: initial;
  }
}

.three-d {
  transform: perspective(75em) rotateX(-1deg);
  border-radius: 10px;
  border: 1px solid;
  border-color: rgb(213, 220, 226) rgb(213, 220, 226) rgb(184, 194, 204);
  transition: all 0.3s ease;
}

.back-link {
  display: flex;
  align-items: center;
  width: 14rem;
  text-shadow: 3px 3px 7px rgba(0, 0, 0, 0.8);
  color: rgba(255, 255, 255, 0.6);
  font-size: 1.25rem;
  margin-bottom: 1.5rem;
}

.portfolio-details {
  z-index: 10;
  position: relative;
  background: radial-gradient(
    rgba(128, 128, 128, 0.223),
    rgba(255, 255, 255, 0.189)
  );
  background-clip: padding-box;
  padding: 3em;
  box-shadow: 0 3px 10px rgba(0, 0, 0, 0.651),
    inset 0 0 20px rgba(255, 255, 255, 0.575);
  margin: 0;
  min-height: 100vh;
  min-width: 50%;
  background-origin: border-box;
  text-shadow: 3px 3px 7px rgba(0, 0, 0, 0.8);
  color: rgba(255, 255, 255, 0.6);
  h2 {
    margin-bottom: 0.5rem;
  }
  p {
    margin-bottom: 0.5rem;
    background: rgba(255, 255, 255, 0.44);
    padding: 0.5rem;
    border-radius: 5px;
    margin-right: 1rem;
    color: white;
  }

  @extend .three-d;

  @media (min-width: 900px) {
    margin: 5em 20% auto;
    min-height: 50%;
  }
}
.portfolio-details::after {
  position: absolute;
  top: -2px;
  bottom: -1px;
  left: -2px;
  right: -1px;
  background: radial-gradient(farthest-corner at 3em 3em, #32323215, #ffffff15);
  content: '';
  z-index: -1;
  border-radius: 6px;
  background-origin: border-box;
}

.title {
  font-family: 'Quicksand', 'Source Sans Pro', -apple-system, BlinkMacSystemFont,
    'Segoe UI', Roboto, 'Helvetica Neue', Arial, sans-serif;
  display: block;
  font-weight: 300;
  font-size: 100px;
  color: #fff;
  text-shadow: 1px 1px 1px rgba(100, 100, 100, 0.4);
  letter-spacing: 1px;
  height: 125px;
}

.subtitle {
  font-weight: 300;
  font-size: 42px;
  color: #526488;
  word-spacing: 5px;
  padding-bottom: 15px;
}

.links {
  padding-top: 15px;
  text-align: center;
}

.link-container {
  display: flex;
  justify-content: space-between;
  align-items: flex-end;
  // flex-wrap: wrap;

  // @media (min-width: 1300px) {
  //   flex-wrap: nowrap;
  // }

  // @media (min-width: 1300px) {
  //   flex-wrap: nowrap;
  // }
}

.container-content {
  display: flex;
  width: 100%;
  flex-wrap: wrap;
  justify-content: space-between;
}
.container-a {
  display: flex;
  flex-basis: 100%;

  flex-wrap: wrap;
  margin: 2rem 0;
  @media (min-width: 1300px) {
    flex-basis: 33.33%;
  }
  > * {
    width: 100%;
  }
}

.container-b {
  display: flex;
  flex-basis: 100%;
  flex-wrap: wrap;
  margin: 0;
  justify-content: flex-end;
  @media (min-width: 1300px) {
    flex-basis: calc(66.66% - 2.55rem);
    margin: 1.25rem 0 1.25rem 1.25rem;
  }
}
img {
  width: 100%;
  border-radius: 10px;
}
</style>
