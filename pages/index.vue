<template>
  <div class="container">
    <h1 class="title">Justin Gaba</h1>
    <PortfolioSelector image></PortfolioSelector>
  </div>
</template>

<script>
export default {}
</script>

<style scoped lang="scss">
.container {
  margin: 0 auto;
  min-height: 100vh;
  display: flex;
  justify-content: center;
  text-align: center;
  flex-wrap: wrap;
  align-content: flex-start;
  background: black;
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
}
</style>
