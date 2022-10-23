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
          :autoplay="{
            delay: 2500,
            disableOnInteraction: false,
          }"
          :speed="800"
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

            <div class="header-swiper-img-box" >
              <img :src="slide.img" alt="" class="header-swiper-img" 
              :class="`header-swiper-img-${idx + 1}`" />

              <img :src="icon.url" alt="" class="header-swiper-icon" v-for="(icon, idd) in slide.icons" :key="idd" :class="`swiper-icon-${idd + 1}`">
            </div>

          </swiper-slide>
        </swiper>

        <span class="vector-left-small vector-left"></span>
        <span class="vector-left-medium vector-left"></span>
        <span class="vector-left-big vector-left"></span>

        <span class="vector-right-small vector-right"></span>
        <span class="vector-right-medium vector-right"></span>
        <span class="vector-right-sm-medium vector-right"></span>
        <span class="vector-right-big vector-right"></span>
      </div>
    </div>
  </header>

  <main class="main">

    <Calculator/>

  </main>

</template>

<script>
import Nav from "@/components/Nav.vue";
import { Swiper, SwiperSlide } from "swiper/vue";
import { Navigation, Pagination, Autoplay } from "swiper";

import "swiper/scss";
import "swiper/scss/navigation";
import "swiper/scss/pagination";

import Calculator from '@/components/Calculator.vue';

export default {
  name: "Home",
  components: {
    Nav,
    Swiper,
    SwiperSlide,
    Calculator
  },
  data() {
    return {
      modules: [Navigation, Pagination, Autoplay],
      headerSwiper: [
        {
          img: require("@/assets/images/home/header/slider/slide-img-1.png"),
          desc: {
            title: "Инвестируйте с повышенной доходностью до <span>19%</span> годовых",
            text: "100% обеспеченность активами, прибыль каждые 3 месяца!",
          },
          icons: [
            {
              url: require('@/assets/images/home/header/slider/icon-17.svg')
            },
            {
              url: require('@/assets/images/home/header/slider/bubbles-icon.svg')
            }
          ]
        },
        {
          img: require("@/assets/images/home/header/slider/slide-img-2.png"),
          desc: {
            title: "Максимальная доля прибыли по вкладам <span>НурФинанс</span>",
            text: "Инвестор получает наибольший капитализированный доход",
          },
          icons: [
            {
              url: require('@/assets/images/home/header/slider/toys-icon.svg')
            }
          ]
        },
      ],
      rangeInp: 0
    };
  },
};
</script>

<style lang="scss" scoped>

.header {
  width: 100%;
  height: 100%;
  background: #f0f4f8;

  .row {
    position: relative;

    & > .vector-left {
      position: absolute;
      top: 0;
      left: -10%;
      min-width: 70px;
      max-width: 70px;
      width: 100%;
      min-height: 130px;
      max-height: 130px;
      height: 100%;
      background: linear-gradient(0deg, rgba(96, 170, 251, 0.2), rgba(96, 170, 251, 0.2)), linear-gradient(126.6deg, rgba(255, 255, 255, 0.12) 28.69%, rgba(255, 255, 255, 0) 100%);
      backdrop-filter: blur(13px);
      border-radius: 60px 0;

      &.vector-left-small {
        top: 0;
        left: -5%;
        min-width: 28px;
        max-width: 28px;
        width: 100%;
        min-height: 55px;
        max-height: 55px;
        height: 100%;
      }

      &.vector-left-medium {
        top: 14%;
        left: -14%;
        min-width: 70px;
        max-width: 70px;
        width: 100%;
        min-height: 130px;
        max-height: 130px;
        height: 100%;
        z-index: 4;
      }

      &.vector-left-big {
        top: 25%;
        left: -12%;
        min-width: 75px;
        max-width: 75px;
        width: 100%;
        min-height: 220px;
        max-height: 220px;
        height: 100%;
      }
    }
    
    & > .vector-right {
      position: absolute;
      top: 0;
      right: -10%;
      min-width: 70px;
      max-width: 70px;
      width: 100%;
      min-height: 130px;
      max-height: 130px;
      height: 100%;
      background: linear-gradient(0deg, rgba(96, 170, 251, 0.2), rgba(96, 170, 251, 0.2)), linear-gradient(126.6deg, rgba(255, 255, 255, 0.12) 28.69%, rgba(255, 255, 255, 0) 100%);
      backdrop-filter: blur(13px);
      border-radius: 60px 0;

      &.vector-right-small {
        top: 25%;
        right: -18%;
        min-width: 28px;
        max-width: 28px;
        width: 100%;
        min-height: 55px;
        max-height: 55px;
        height: 100%;
      }

      &.vector-right-sm-medium {
        top: 5%;
        right: -11%;
        min-width: 55px;
        max-width: 55px;
        width: 100%;
        min-height: 105px;
        max-height: 105px;
        height: 100%;
        z-index: 4;
      }

      &.vector-right-medium {
        top: unset;
        bottom: 15%;
        right: -14%;
        min-width: 48px;
        max-width: 48px;
        width: 100%;
        min-height: 150px;
        max-height: 150px;
        height: 100%;
        z-index: 4;
      }

      &.vector-right-big {
        top: 13%;
        right: -9%;
        min-width: 95px;
        max-width: 95px;
        width: 100%;
        min-height: 195px;
        max-height: 195px;
        height: 100%;
        border-radius: 85px 0;
      }
    }
  }

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

  .header-swiper-img-box {
    max-width: 460px;
    width: 100%;
    max-height: 460px;
    position: relative;
    display: grid;
    place-items: center;

    .header-swiper-icon {
      position: absolute;
      top: 0;
      left: 0;
      width: 100%;
      z-index: -1;

      &.swiper-icon-1 {
        backdrop-filter: blur(5px);
        top: 5%;
      }

      &.swiper-icon-2 {
        z-index: -2;
      }
    }
  }

  .header-swiper-img {
    width: 100%;
    height: 100%;
    object-fit: cover;
    object-position: top;

    &.header-swiper-img-2 {
      max-width: 275px;
    }
  }
}

.main {
  width: 100%;
  display: flex;
  flex-direction: column;
  row-gap: 120px;
  padding: 60px 0;
}



</style>
