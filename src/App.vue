<template>
  <div id="app">
    <header><h1>My banner carousel</h1></header>
    <BannerCarousel/>
  </div>
</template>

<script>
import BannerCarousel from './components/BannerCarousel';

export default {
  name: 'app',
  components: {
    BannerCarousel,
  },
};
</script>

<style>
#app {
  font-family: 'Shrikhand', cursive;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
