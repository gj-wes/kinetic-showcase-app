<template>
  <div>
    <mail-header v-if="mobile"></mail-header>
    <section class="kinetic" v-if="kinetic">
      <section>
        <h1>Tap and Flip</h1>
        <p>
          Examples of horizontal, vertical and diagonal flips.
        </p>
      </section>
      <div class="card" :class="{'card--horizontal-flip':flipHorizontal}" @click="flipHorizontal = !flipHorizontal">
        <div class="card__face card__front">
          <img :src="[mobile ? 'https://placehold.co/375x320/7763c6/ffffff?text=Horizontal+Flip+.+Card+front' : 'https://placehold.co/600x320/7763c6/ffffff?text=Horizontal+Flip+.+Card+front']" alt="" class="card__image">
        </div>
        <div class="card__face card__back">
          <h4>Horizontal flip</h4>
          <p>This is the backface content<br><br>Lorem ipsum dolor sit amet consectetur adipisicing elit. Ab aspernatur sint exercitationem consectetur veniam odit?</p>
        </div>
      </div>
      <div class="card" :class="{'card--vertical-flip':flipVertical}" @click="flipVertical = !flipVertical">
        <div class="card__face card__front">
          <img :src="[mobile ? 'https://placehold.co/375x320/f78e03/ffffff?text=Vertical+Flip+.+Card+front' : 'https://placehold.co/600x320/f78e03/ffffff?text=Vertical+Flip+.+Card+front']" alt="" class="card__image">
        </div>
        <div class="card__face card__back card__back--vertical">
          <h4>Vertical flip</h4>
          <p>This is the backface content<br><br>Lorem ipsum dolor sit amet consectetur adipisicing elit. Ab aspernatur sint exercitationem consectetur veniam odit?</p>
        </div>
      </div>
      <div class="card" :class="{'card--diagonal-flip':flipDiagonal}" @click="flipDiagonal = !flipDiagonal">
        <div class="card__face card__front">
          <img :src="[mobile ? 'https://placehold.co/375x320/ef332b/ffffff?text=Diagonal+Flip+.+Card+front' : 'https://placehold.co/600x320/ef332b/ffffff?text=Diagonal+Flip+.+Card+front']" alt="" class="card__image">
        </div>
        <div class="card__face card__back card__back--diagonal">
          <h4>Diagonal flip</h4>
          <p>This is the backface content<br><br>Lorem ipsum dolor sit amet consectetur adipisicing elit. Ab aspernatur sint exercitationem consectetur veniam odit?</p>
        </div>
      </div>
    </section>
    <section class="fallback" v-else>
      <div>
        <img src="https://placehold.co/600x320?text=Image" alt="" class="card__image">
        <div class="card__content">
          <h4>Horizontal flip</h4>
          <p>This is the backface content<br><br>Lorem ipsum dolor sit amet consectetur adipisicing elit. Ab aspernatur sint exercitationem consectetur veniam odit?</p>
        </div>
      </div>
      <div>
        <img src="http://placekitten.com/600/320" alt="" class="card__image">
        <div class="card__content">
          <h4>Vertical flip</h4>
          <p>This is the backface content<br><br>Lorem ipsum dolor sit amet consectetur adipisicing elit. Ab aspernatur sint exercitationem consectetur veniam odit?</p>
        </div>
      </div>
      <div>
        <img src="http://unsplash.it/g/600/320?random&gravity=center" alt="" class="card__image">
        <div class="card__content">
          <h4>Diagonal flip</h4>
          <p>This is the backface content<br><br>Lorem ipsum dolor sit amet consectetur adipisicing elit. Ab aspernatur sint exercitationem consectetur veniam odit?</p>
        </div>
      </div>
    </section>
  </div>
</template>

<script>
import MailHeader from "./MailHeader.vue";
export default {
  name: "TapAndFlip",
  components: {
    "mail-header": MailHeader
  },
  props: {
    isKineticView: Boolean,
    isMobile: Boolean
  },
  data() {
    return {
      kinetic: true,
      mobile: false,
      flipHorizontal: false,
      flipVertical: false,
      flipDiagonal: false
    };
  },
  watch: {
    isKineticView() {
      this.kinetic = this.isKineticView;
    },
    isMobile() {
      this.mobile = this.isMobile;
    }
  }
};
</script>

<style scoped>
.kinetic {
  perspective: 2000px;
}

.card {
  /* Adjust speed of flip here */
  transition: all 0.6s ease-in-out;
  transform-style: preserve-3d;
  height: 320px;
  position: relative;
}
.card__face {
  backface-visibility: hidden;
  transform-style: preserve-3d;
  height: 320px;
  position: absolute;
}

.card__front {
  transform: rotateY(0deg);
}

.card__back {
  transform: rotateY(180deg);
  background-color: lightgray;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
}

.card--horizontal-flip {
  transform: rotateY(-180deg);
}

.card__back--vertical {
  transform: rotateY(180deg) rotateZ(180deg);
}

.card--vertical-flip {
  transform-origin: 100% 160px;
  transform: rotateX(-180deg);
}

.card__back--diagonal {
  transform: rotateY(180deg) rotateZ(90deg);
}
.card--diagonal-flip {
  transform: rotate3d(-1, -1, 0, 180deg);
}

img {
  max-width: 100%;
  height: auto;
}
</style>