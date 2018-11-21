<template>
  <div>
    <p>
      Select an animation:
    </p>
    <select v-model="visibleAnimation">
      <option>Final Score</option>
      <option>Ryder Cup 2018</option>
      <option>Bulletproof</option>
    </select>
    <div :is="visibleAnimation" :is-kinetic-view="kinetic" :is-mobile="mobile"></div>
  </div>
</template>
<script>
import FinalScoreAnimation from './animation_examples/final_score/FinalScore.vue';
import RyderCupAnimation from './animation_examples/ryder_cup/RyderCup.vue';
import BulletproofAnimation from './animation_examples/bltprf/Bulletproof.vue';
export default {
  name: "CSSAnim",
  components: {
    "Final Score": FinalScoreAnimation,
    "Ryder Cup 2018": RyderCupAnimation,
    "Bulletproof": BulletproofAnimation
  },
  props: {
    isKineticView: Boolean,
    isMobile: Boolean
  },
  data() {
    return {
      kinetic: true,
      mobile: false,
      animationsArray: ["Final Score", "Ryder Cup 2018", "Bulletproof"],
      visibleAnimation: "Final Score"
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
  p {
    margin-bottom: 0;
  }
  select {
    margin: 5px 0 1rem 0;
  }
</style>
