<template>
    <div>
        <slick ref="slick" :options="slickOptions" class="banner-carousel">
            <a href="https://img00.deviantart.net/e88c/i/2013/072/9/b/space_frontier__heimdall_by_nathanblackwolf-d5xvzxg.jpg">
                <img class="banner-image" data-lazy="https://img00.deviantart.net/e88c/i/2013/072/9/b/space_frontier__heimdall_by_nathanblackwolf-d5xvzxg.jpg" alt="">
            </a>
            <a href="https://d1w9csuen3k837.cloudfront.net/Pictures/1280x720/9/9/2/132992_shutterstock_576050593.jpg">
                <img class="banner-image" data-lazy="https://d1w9csuen3k837.cloudfront.net/Pictures/1280x720/9/9/2/132992_shutterstock_576050593.jpg" alt="">
            </a>
        </slick>
    </div>
</template>
<script>
import Slick from 'vue-slick';
export default {
  name: 'BannerCarousel',
  components: { Slick },
  data() {
    return {
      slickOptions: {
        //options can be used from the plugin documentation
        slidesToShow: 1,
        infinite: true,
        accessibility: true,
        adaptiveHeight: false,
        // arrows: true,
        // dots: true,
        // draggable: true,
        edgeFriction: 0.3,
        swipe: true,
        lazyLoad: 'ondemand',
      },
    };
  },
  // All slick methods can be used too, example here
  methods: {
    next() {
      this.$refs.slick.next();
    },
    prev() {
      this.$refs.slick.prev();
    },
    reInit() {
      // Helpful if you have to deal with v-for to update dynamic lists
      this.$refs.slick.reSlick();
    },
  },
};
</script>

<style>
.slick-prev:before,
.slick-next:before {
  font-size: 20px;
  line-height: 1;
  opacity: 0.75;
  color: black;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
}
.slick-arrow {
  background: red;
}
.slick-next:before {
  content: '>';
}
.slick-prev:before {
  content: '<';
}

.slick-next {
  right: -25px;
}
.slick-prev {
  left: -25px;
}
.slick-slider {
  width: 544px;
  margin: 30px auto 50px;
}
.slick-prev,
.slick-next {
  font-size: 0;
  line-height: 0;
  position: absolute;
  top: 50%;
  display: block;
  width: 20px;
  height: 20px;
  padding: 0;
  -webkit-transform: translate(0, -50%);
  -ms-transform: translate(0, -50%);
  transform: translate(0, -50%);
  cursor: pointer;
  color: transparent;
  border: none;
  outline: none;
  background: transparent;
}
.banner-image {
  width: 544px;
}
</style>
