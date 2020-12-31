<template>
  <div class="main">
    <div class="bg1"></div>
    <Nuxt />
  </div>
</template>

<style lang="scss">
html {
  font-family: 'Source Sans Pro', -apple-system, BlinkMacSystemFont, 'Segoe UI',
    Roboto, 'Helvetica Neue', Arial, sans-serif;
  font-size: 16px;
  word-spacing: 1px;
  -ms-text-size-adjust: 100%;
  -webkit-text-size-adjust: 100%;
  -moz-osx-font-smoothing: grayscale;
  -webkit-font-smoothing: antialiased;
  box-sizing: border-box;
}

*,
*::before,
*::after {
  box-sizing: border-box;
  margin: 0;
}
.main {
  // background: black;
  display: flex;
  justify-content: center;
}
.bg {
  position: fixed;
  width: 100%;
  height: calc(100vh);
  // background: black;
  -webkit-filter: grayscale(0.33) blur(5px) brightness(60%);
  -moz-filter: grayscale(0.33) blur(5px) brightness(50%);
  -o-filter: grayscale(0.33) blur(5px) brightness(50%);
  -ms-filter: grayscale(0.33) blur(5px) brightness(50%);
  filter: grayscale(0.33) blur(5px) brightness(50%);
  transform: scale(1.1);
}
.bg1 {
  margin: 0 auto;
  min-height: 100vh;
  min-width: 100vw;
  display: flex;
  justify-content: center;
  // text-align: center;
  flex-wrap: wrap;
  // align-content: center;
  background-image: url('~assets/bg3.jpg');
  background-size: cover;
  @extend .bg;
}
.portfolio-selector2 {
  background-image: url('~assets/bg1.jpg');
  background-size: cover;
}
</style>
