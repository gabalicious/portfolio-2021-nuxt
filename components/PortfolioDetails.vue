<template>
  <div class="portfolio-details">
    <h2>{{ option.title }}</h2>
    <p>
      {{ option.description }}
    </p>
    <div class="link-container">
      <a href="#" class="circle-link">
        <font-awesome-icon
          :style="{ color: 'inherit' }"
          :icon="['fab', 'github-alt']"
        />
        <label for="">Browse Code</label>
      </a>
      <a href="#" class="circle-link">
        <font-awesome-icon
          :style="{ color: 'inherit' }"
          :icon="['fas', 'external-link-alt']"
        />
        <label for="">Preview External Demo </label>
      </a>
      <a href="#" class="circle-link">
        <font-awesome-icon
          :style="{ color: 'inherit' }"
          :icon="['fas', 'link']"
        />
        <label for="">Preview Internal Iframe Demo </label>
      </a>
    </div>
  </div>
</template>
<script>
export default {
  props: {
    option: {
      type: Object,
      default() {
        return {
          title: 'Test',
          description:
            'Tech virtual drone online browser platform through in a system. But stream software offline. Professor install angel sector anywhere create at components smart. ',
        }
      },
    },
  },
  data() {
    return {}
  },
}
</script>

<style lang="scss" scoped>
.portfolio-details {
  font-family: 'Heebo', sans-serif !important;
  -webkit-font-smoothing: antialiased;
  position: relative;
  z-index: 2;
  width: 50%;
  background-color: rgba(255, 255, 255, 0.05);
  display: flex;
  flex-wrap: wrap;
  padding: 1.5em;
  h2 {
    color: rgb(216, 61, 29);
    font-size: 16px;
    margin-bottom: 0.5em;
  }
  p {
    font-size: 12px;
    width: 100%;
    color: #9ca4ab;
    text-align: left;
    line-height: 1.6;
  }
  .link-container {
    width: 100%;
    display: flex;
    justify-content: center;
    align-items: flex-end;
  }
  .circle-link {
    // padding: 5px;
    background: white;
    width: 30px;
    height: 30px;
    display: flex;
    justify-content: center;
    align-content: center;
    align-items: center;
    text-transform: capitalize;
    border: 1px solid white;
    border-radius: 50%;
    color: orangered;
    label {
      display: none;
    }
  }
  .circle-link + .circle-link {
    margin-left: 5px;
  }
}
</style>
