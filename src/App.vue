<template>
  <div id="app">
    <ImageCarousel
      :item-width="itemWidth"
      :images="[
        require('@/assets/sample-1.png'),
        require('@/assets/sample-2.png'),
        require('@/assets/sample-3.png')
      ]"
    />
  </div>
</template>

<script>
import ImageCarousel from "./components/ImageCarousel.vue";

export default {
  name: "app",
  data: function() {
    return {
      itemWidth: 1034
    };
  },
  components: {
    ImageCarousel
  }
};
</script>

<style>
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
