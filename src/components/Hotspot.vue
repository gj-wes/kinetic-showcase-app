<template>
  <div>
    <mail-header v-if="mobile"></mail-header>
    <section class="kinetic" v-if="kinetic">
      <section class="spots" :class="{'content--is-mobile': mobile, 'spots__content--is-open': isPodOpen}">
        <div @click="showPod1" :class="{'spots--mobile': mobile}"><img src="https://placehold.it/150x150" alt=""><div class="indicator">+</div></div>
        <div @click="showPod2" :class="{'spots--mobile': mobile}"><img src="https://placehold.it/150x150" alt=""><div class="indicator">+</div></div>
        <div @click="showPod3" :class="{'spots--mobile': mobile}"><img src="https://placehold.it/150x150" alt=""><div class="indicator">+</div></div>
      </section>
      <section class="content content__kinetic" :class="{'content--is-mobile': mobile, 'content--is-open': pod1Visible}">
        <img src="https://placehold.it/300x300?text=Pod1+Image" alt="">
        <div>
          <div class="close" @click="closePod">X</div>
          <h3>Lorem, ipsum dolor.</h3>
          <p>Lorem, ipsum dolor sit amet consectetur adipisicing elit. Voluptate, pariatur!</p>
        </div>
      </section>
      <section class="content content__kinetic" :class="{'content--is-mobile': mobile, 'content--is-open': pod2Visible}">
        <img src="https://placehold.it/300x300?text=Pod2+Image" alt="">
        <div>
          <div class="close" @click="closePod">X</div>
          <h3>Nulla, facere maxime.</h3>
          <p>Saepe, cupiditate modi nesciunt aperiam consequatur blanditiis debitis obcaecati pariatur?</p>
        </div>
      </section>
      <section class="content content__kinetic" :class="{'content--is-mobile': mobile, 'content--is-open': pod3Visible}">
        <img src="https://placehold.it/300x300?text=Pod3+Image" alt="">
        <div>
          <div class="close" @click="closePod">X</div>
          <h3>Fugit, earum sint.</h3>
          <p>Nam voluptatibus aspernatur corrupti commodi ipsam iste praesentium quis veniam!</p>
        </div>
      </section>
    </section>
    <section class="fallback" v-else>
      <section class="content" :class="{'content--is-mobile': mobile}">
        <img src="https://placehold.it/300x300?text=Pod1+Image" alt="">
        <div>
          <h3>Lorem, ipsum dolor.</h3>
          <p>Lorem, ipsum dolor sit amet consectetur adipisicing elit. Voluptate, pariatur!</p>
        </div>
      </section>
      <section class="content" :class="{'content--is-mobile': mobile}">
        <img src="https://placehold.it/300x300?text=Pod2+Image" alt="">
        <div>
          <h3>Nulla, facere maxime.</h3>
          <p>Saepe, cupiditate modi nesciunt aperiam consequatur blanditiis debitis obcaecati pariatur?</p>
        </div>
      </section>
      <section class="content" :class="{'content--is-mobile': mobile}">
        <img src="https://placehold.it/300x300?text=Pod3+Image" alt="">
        <div>
          <h3>Fugit, earum sint.</h3>
          <p>Nam voluptatibus aspernatur corrupti commodi ipsam iste praesentium quis veniam!</p>
        </div>
      </section>
    </section>
  </div>
</template>

<script>
import MailHeader from "./MailHeader.vue";
export default {
  name: 'Hotspot',
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
      isPodOpen: false,
      pod1Visible: false,
      pod2Visible: false,
      pod3Visible: false
    }
  },
  methods: {
    showPod1() {
      this.pod1Visible = true;
      this.isPodOpen = true;
    },
    showPod2() {
      this.pod2Visible = true;
      this.isPodOpen = true;
    },
    showPod3() {
      this.pod3Visible = true;
      this.isPodOpen = true;
    },
    closePod() {
      this.isPodOpen = false;
      this.pod1Visible = false;
      this.pod2Visible = false;
      this.pod3Visible = false;
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
  .content {
    display: flex;
  }
  .content--is-mobile {
    flex-direction: column;
  }
  .content img {
    max-width: 100%;
    min-width: 300px;
    height: auto;
  }
  .content div {
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    position: relative;
  }
  .content:nth-of-type(1) {
    background-color:lightyellow;
  }
  .content:nth-of-type(2) {
background-color: coral
  }
  .content:nth-of-type(3) {
background-color: lightblue
  }
  .content .close {
    position: absolute;
    top: 10px;
    right: 10px;
    width: 30px;
    height: 30px;
  }

  .spots {
    display: flex;
    justify-content: space-around;
    align-items: center;
    padding: 30px;
  }
  .spots div {
    position: relative;
  }
  .spots div .indicator {
    position: absolute;
    top: -15px;
    right: -15px;
    width: 40px;
    height: 40px;
    border-radius: 50%;
    color: white;
    background-color: red;
    font-size: 35px;
    font-weight: bold;
    text-align: center;
    line-height: 38px;
    vertical-align: middle;
    font-weight: bold;
    cursor: pointer;
  }
  .spots__content--is-open {
    display: none;
  }
  .spots--mobile {
    margin-bottom: 10px;
  }

  .content__kinetic {
    display: none;
  }
  .content--is-open {
    display: flex;
  }
</style>