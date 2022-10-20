<template>
  <Nav />

  <header class="header">
    <div class="container">
      <div class="row">

        <swiper
          :navigation="true"
          :pagination="true"
          :modules="modules"
          class="home-header-swiper"
          :spaceBetween="10"
        >
          <swiper-slide
            class="header-swiper-slide"
            v-for="(slide, idx) in headerSwiper"
            :key="idx"
          >
            <div class="header-swiper-desc">
              <h1 class="swiper-desc-title" v-html="slide.desc.title">
              </h1>
              <p class="swiper-desc-text" v-html="slide.desc.text">
              </p>
            </div>

            <img :src="slide.img" alt="" class="header-swiper-img" />
          </swiper-slide>
        </swiper>

      </div>
    </div>
  </header>

  <main class="main">
    <section class="product__section">
      <div class="container">
        <div class="row"></div>
      </div>
    </section>
  </main>
</template>

<script>
import Nav from "@/components/Nav.vue";
import { Swiper, SwiperSlide } from "swiper/vue";
import { Navigation, Pagination } from "swiper";

import "swiper/scss";
import "swiper/scss/navigation";
import "swiper/scss/pagination";

export default {
  name: "Home",
  components: {
    Nav,
    Swiper,
    SwiperSlide,
  },
  data() {
    return {
      modules: [Navigation, Pagination],
      headerSwiper: [
        {
          img: require("@/assets/images/home/header/slider/slide-img-1.png"),
          desc: {
            title: "Инвестируйте с повышенной доходностью до <span>19%</span> годовых",
            text: "100% обеспеченность активами, прибыль каждые 3 месяца!",
          },
        },
        {
          img: require("@/assets/images/home/header/slider/slide-img-2.png"),
          desc: {
            title: "Максимальная доля прибыли по вкладам <span>НурФинанс</span>",
            text: "Инвестор получает наибольший капитализированный доход",
          },
        },
      ],
    };
  },
};
</script>

<style lang="scss" scoped>
.header {
  width: 100%;
  min-height: 450px;
  height: 100%;
  background: #f0f4f8;
}

.home-header-swiper {
  width: 100%;
  margin-top: 60px;

  .header-swiper-slide {
    width: 100%;
    display: flex;
    gap: 20px;
  }

  .header-swiper-desc {
    max-width: 665px;
    width: 100%;
    display: flex;
    flex-direction: column;
    row-gap: 20px;

    .swiper-desc-title {
      font-size: 40px;
      font-weight: 700;
      color: var(--nfc-black);
    }

    .swiper-desc-text {
      font-size: 15px;
      font-weight: 400;
      color: var(--nfc-black);
    }
  }

  .header-swiper-img {
    max-width: 430px;
    width: 100%;
    max-height: 430px;
    object-fit: cover;
    object-position: top;
  }
}



</style>
