<template>
  <div class="banners">
    <slick
      ref="slick"
      :options="slickOptions"
      class="banner-carousel"
      @afterChange="handleAfterChange"
    >
      <a v-for="item in images" :href="item.src" :key="item.id">
        <img class="banner-image" :data-lazy="item.src" alt="" />
      </a>
    </slick>
    <div ref="buttons" class="banner-buttons">
      <button data-id="0" class="banner-button" v-on:click="setPosition(0)">
        banner1
      </button>
      <button data-id="1" class="banner-button" v-on:click="setPosition(1)">
        banner2
      </button>
    </div>
  </div>
</template>
<script>
import Slick from "vue-slick";

function activateButton(position) {
  Array.from(this.$refs.buttons.children).forEach(elem => {
    if (Number(elem.attributes["data-id"].value) === position) {
      elem.classList.add("banner-button__active");
    } else {
      elem.classList.remove("banner-button__active");
    }
  });
}

export default {
  name: "BannerCarousel",
  components: { Slick },
  data() {
    return {
      images: [
        {
          id: 0,
          src:
            "https://img00.deviantart.net/e88c/i/2013/072/9/b/space_frontier__heimdall_by_nathanblackwolf-d5xvzxg.jpg"
        },
        {
          id: 1,
          src:
            "https://d1w9csuen3k837.cloudfront.net/Pictures/1280x720/9/9/2/132992_shutterstock_576050593.jpg"
        }
      ],
      slickOptions: {
        //options can be used from the plugin documentation
        slidesToShow: 1,
        infinite: true,
        accessibility: true,
        adaptiveHeight: false,
        autoplay: true,
        arrows: false,
        // dots: true,
        // draggable: true,
        edgeFriction: 0.3,
        swipe: true,
        lazyLoad: "ondemand"
      }
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
    handleAfterChange(slick, current, next) {
      activateButton.call(this, next);
    },
    setPosition(position) {
      activateButton.call(this, position);

      this.$refs.slick.goTo(position, true);
    }
  }
};
</script>

<style>
.slick-slider {
  margin: 30px auto 0;
}

.slick-slide img {
  height: 100%;
  width: 100%;
}

.slick-slider .slick-track,
.slick-slider .slick-list {
  height: 13vw;
  width: 544px;
}
</style>
<style scoped>
.banners {
  display: flex;
  flex-direction: column;
  align-items: center;
}

.banner-buttons {
  margin-top: 5px;
  width: 544px;
  display: flex;
  height: 40px;
  margin-left: auto;
  margin-right: auto;
  justify-content: space-around;
}

.banner-buttons .banner-button {
  border: 1px solid blue;
  width: 100%;
}

.banner-buttons .banner-button__active {
  border-top: 2px solid yellow;
}
</style>
