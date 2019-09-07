<template>
  <div class="image-carousel">
    <div class="image-carousel__previous" @click="onPreviousClick">前へ</div>
    <div class="image-carousel__next" @click="onNextClick">次へ</div>
    <div
      class="image-carousel__body"
      v-bind:style="{ width: itemWidth + 'px' }"
    >
      <transition-group
        name="image-carousel__list"
        tag="div"
        class="image-carousel__container"
        v-bind:style="{
          width: wholeWidth + 'px',
          marginLeft: leftMargin + 'px'
        }"
      >
        -->
        <figure
          v-for="(image, _i) in imageList"
          v-bind:key="_i"
          v-bind:style="{ width: itemWidth + 'px' }"
          class="image-carousel__item"
        >
          <img :src="image" class="image-carousel__item__image" />
        </figure>
      </transition-group>
    </div>
  </div>
</template>

<script>
export default {
  name: "ImageCarousel",
  data: function() {
    return {
      currentIndex: 0
    };
  },
  props: {
    itemWidth: Number,
    images: Array
  },
  computed: {
    imageList() {
      return this.images;
    },
    wholeWidth() {
      return this.itemWidth * this.imageList.length;
    },
    leftMargin() {
      return this.currentIndex * -1 * this.itemWidth;
    }
  },
  methods: {
    onPreviousClick() {
      this.displayPrevious();
    },
    onNextClick() {
      this.displayNext();
    },
    displayPrevious() {
      --this.currentIndex;
    },
    displayNext() {
      ++this.currentIndex;
    }
  }
};
</script>

<style scoped>
.image-carousel__body {
  overflow: hidden;
  margin: 0px auto;
}
.image-carousel__container {
  height: 580px;
  transition: all 500ms linear 0s;
}
.image-carousel__item {
  margin: 0px 0px;
  display: inline-block;
}
</style>
