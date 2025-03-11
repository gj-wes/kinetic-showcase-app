<template>
  <div>
    <mail-header v-if="mobile"></mail-header>
    <section class="kinetic" v-if="kinetic" :class="{'kinetic--is-mobile':mobile}">
      <div class="controls" :class="{'controls--is-mobile':mobile}">
        <div class="button" @click="showPod1"></div>
        <div class="button" @click="showPod2"></div>
        <div class="button" @click="showPod3"></div>
      </div>
      <div class="content">
        <div class="content__pod" :class="{'content__pod--visible': pod1Visible, 'content__pod--center-text': mobile}">
          <h2>Lorem, ipsum dolor.</h2>
          <p>Lorem ipsum dolor sit amet consectetur adipisicing elit. Cupiditate repellat vero eius exercitationem autem illum eveniet itaque, non recusandae ratione.</p>
        </div>
        <div class="content__pod" :class="{'content__pod--visible': pod2Visible, 'content__pod--center-text': mobile}">
          <h2>Possimus, impedit pariatur!</h2>
          <p>Lorem, ipsum dolor sit amet consectetur adipisicing elit. Doloribus ipsa aspernatur architecto dolores adipisci suscipit eos labore porro nostrum distinctio.</p>
        </div>
        <div class="content__pod" :class="{'content__pod--visible': pod3Visible, 'content__pod--center-text': mobile}">
          <h2>Nemo, earum hic!</h2>
          <p>Lorem ipsum dolor sit amet, consectetur adipisicing elit. Harum, odit delectus! Iste provident temporibus a repudiandae suscipit, quidem aliquid saepe.</p>
        </div>
      </div>
    </section>
    <section class="fallback" v-else>
      <img src="https://placehold.co/600x350?text=Fallback+GIF" alt="">
    </section>
    <section>
      <h1>Button Carousel</h1>
      <p>
        Lorem ipsum dolor sit amet consectetur adipisicing elit. Delectus, repellat!
      </p>
    </section>
  </div>
</template>

<script>
import MailHeader from "./MailHeader.vue";
export default {
  name: 'CarouselButtons',
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
      pod1Visible: true,
      pod2Visible: false,
      pod3Visible: false
    }
  },
  methods: {
    showPod1() {
      this.pod1Visible = true;
      this.pod2Visible = false;
      this.pod3Visible = false;
    },
    showPod2() {
      this.pod1Visible = false;
      this.pod2Visible = true;
      this.pod3Visible = false;
    },
    showPod3() {
      this.pod1Visible = false;
      this.pod2Visible = false;
      this.pod3Visible = true;
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
    position: relative;
    min-height: 300px;
    display: flex;
    flex-direction: row-reverse;
    background-image: linear-gradient(rgba(0,0,0,0.4), rgba(0, 0, 0, 0.4)), url('https://placehold.co/600x300?text=Background');
    background-size: 100% 100%;
  }
  .kinetic--is-mobile {
    flex-direction: column;
    min-height: 320px;
  }
  .controls {
    display: flex;
    flex-direction: column;
    justify-content: space-around;
    align-items: center;
    padding: 10px;
    background-image: linear-gradient(rgba(0,0,0,0.5), rgba(0,0,0,0.5));
  }
  .controls--is-mobile {
    flex-direction: row;
  }
  .button {
    width: 50px;
    height: 50px;
    border-radius: 5px;
    background-color: orangered
  }
  .button:hover {
    background-color: orange;
  }

  .content {
    display: flex;
    justify-content: center;
    align-items: center;
  }

  .content__pod {
    display: none;
    text-align: left;
    color: white;
    padding: 20px;
    animation: fadeIn 0.3s linear;
  }
  .content__pod--center-text {
    text-align: center;
  }
  .content__pod--visible {
    display: block;
  }
  @keyframes fadeIn {
    from {opacity: 0;}
    to {opacity: 1;}
  }
  .fallback img {
    max-width: 100%;
    height: auto;
  }
</style>