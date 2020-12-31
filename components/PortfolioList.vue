<template>
  <div class="portfolio-list">
    <div v-for="(opt, i) in current" :key="i" class="portfolio-card" :j="i">
      <h3>{{ opt.name }}</h3>

      <p>{{ opt.short || '' }}</p>
      <PortfolioButton :cat="cat()" :option="opt" :index="i">
        Open Details
      </PortfolioButton>
    </div>
  </div>
</template>
<script>
export default {
  props: {
    current: {
      type: Array,
      default() {
        return []
      },
    },
    cat: {
      type: Function,
      default() {
        return 0
      },
    },
  },
}
</script>

<style lang="scss">
.portfolio-list {
  position: relative;
  display: flex;
  align-content: flex-start;
  // justify-content: center;
  flex-wrap: wrap;
  z-index: 2;
  width: 100%;
  min-height: 200px;
  @media (min-width: 900px) {
    margin: 0 20%;
  }
  @media (min-width: 1300px) {
    margin: unset;
  }
}

.three-d {
  transform: perspective(75em) rotateX(-5deg);
  border-radius: 10px;
  border: 1px solid;
  border-color: rgb(213, 220, 226) rgb(213, 220, 226) rgb(184, 194, 204);
  transition: all 0.3s ease;
}

.three-d:hover {
  transform: perspective(75em) rotateX(4deg) rotateY(4deg);
}

.portfolio-card {
  z-index: 10;
  position: relative;
  background: radial-gradient(
    rgba(128, 128, 128, 0.223),
    rgba(255, 255, 255, 0.189)
  );
  background-clip: padding-box;
  padding: 1em;
  box-shadow: 0 3px 10px rgba(0, 0, 0, 0.651),
    inset 0 0 20px rgba(255, 255, 255, 0.575);
  width: calc(50% - 2rem);
  min-height: 100px;
  background-origin: border-box;
  text-shadow: 3px 3px 7px rgba(0, 0, 0, 0.8);
  color: rgba(255, 255, 255, 0.6);
  margin: 1em;

  h3,
  p {
    margin-bottom: 1em;
  }
  @media (min-width: 1100px) {
    width: 300px;

    margin-right: auto;
    margin-left: 3%;
  }
  @extend .three-d;
}
.portfolio-card::after {
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
</style>
