<template>
  <div>
    <mail-header v-if="mobile"></mail-header>
    <section class="kinetic" v-if="kinetic">
      <div class="slides" :style="{transform: 'translateX('+slideTranslate+'%)'}">
        <div class="slide">
          <img src="https://via.placeholder.com/600x350?text=Slide+1" alt="">
          <div class="right" @click="slideTrack('-25')">&gt;</div>
        </div>
        <div class="slide">
          <img src="https://via.placeholder.com/600x350?text=Slide+2" alt="">
          <div class="left" @click="slideTrack('0')">&lt;</div>
          <div class="right" @click="slideTrack('-50')">&gt;</div>
        </div>
        <div class="slide">
          <img src="https://via.placeholder.com/600x350?text=Slide+3" alt="">
          <div class="left" @click="slideTrack('-25')">&lt;</div>
          <div class="right" @click="slideTrack('-75')">&gt;</div>
        </div>
        <div class="slide">
          <img src="https://via.placeholder.com/600x350?text=Slide+4" alt="">
          <div class="left" @click="slideTrack('-50')">&lt;</div>
        </div>
      </div>
    </section>
    <section class="fallback" v-else>
      <img src="https://via.placeholder.com/600x350?text=Fallback+GIF" alt="">
    </section>
    <section>
      <h1>Slider Carousel</h1>
      <p>
        Lorem ipsum dolor sit amet consectetur adipisicing elit. Delectus, repellat!
      </p>
    </section>
  </div>
</template>

<script>
import MailHeader from "./MailHeader.vue";

export default {
  name: 'CarouselSlider',
  components: {
    "mail-header": MailHeader
  },
  props: {
    isKineticView: Boolean,
    isMobile: Boolean
  },
  data() {
    return {
      slideTranslate: '0',
      kinetic: true,
      mobile: false
    }
  },
  methods: {
    slideTrack(val) {
      this.slideTranslate = val;
    }
  },
  watch: {
    isKineticView() {
      this.kinetic = this.isKineticView;
    },
    isMobile() {
      this.mobile = this.isMobile;
    }
  }
}
</script>

<style scoped>
  .kinetic {
    overflow: hidden;
  }
  .slides {
    display: flex;
    width: 400%;
    transition: all 0.4s ease-in-out
  }

  .slide {
    position: relative;
  }

  .slide img,
  .fallback img {
    max-width: 100%;
    height: auto;
    display: block;
  }

  .slide div {
    font-size: 4.5rem;
    color: white;
    position: absolute;
    top: 50%;
    animation: pulse 1.8s linear infinite;
  }

  .slide .left {
    left: 2%;
  }

  .slide .right {
    right: 2%;
  }

  @keyframes pulse {
    0%, 100% { transform: scale(1,1) translateY(-50%)}
    50% { transform: scale(1.2, 1.2) translateY(-50%)}
  }

</style>
