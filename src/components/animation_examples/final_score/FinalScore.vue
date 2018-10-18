<template>
  <div>
    <section class="kinetic" :class="{'mobile--height': mobile}" v-if="kinetic">
      <div class="container" :class="{'mobile--height': mobile}">
        <div class="dave" :class="{'mobile--height': mobile}">
          <img src="./images/dave.png" alt="">
        </div>

        <div class="copy" :class="{'mobile--height': mobile}">
          <img src="./images/copy-overlay.png" alt="">
        </div>

        <div class="logo" :class="{'logo--mobile': mobile}"></div>

      </div>
    </section>
    <section class="fallback" v-else>
      <img src="./images/fallback-gif.gif" alt="FINAL SCORE">
    </section>
    <p>
      An explosive action thriller, FINAL SCORE (Cert 15) is directed by Scott Mann and also stars Pierce Brosnan, Ray Stevenson, Ralph Brown and Amit&nbsp;Shah.
      <br><br>
      A group of heavily armed criminals take control of a stadium packed with 35,000 football fans.  Ex-soldier Michael Knox (Dave Bautista), is forced to use skills from his military background and everything at his disposal to save the spectators, including the life of a fallen comrade's&nbsp;daughter.  
    </p>
  </div>
</template>
<script>
export default {
  name: "FinalScoreAnimation",
  props: {
    isKineticView: Boolean,
    isMobile: Boolean
  },
  data() {
    return {
      kinetic: null,
      mobile: null
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
  .container {
    width: 100%;
    height: 666px;
    position: relative;
    background-image: url('images/kinetic-bg.jpg');
    background-size: 100% 100%;
    overflow: hidden;
  }

  .copy {
    width: 100%;
    height: 666px;
    position: absolute;
    top: 0;
    left: 0;
  }
  .copy img {
    content: url('images/copy-overlay.png');
    max-width: 100%;
  }

  .logo {
    width: 270px;
    height: 170px;
    position: absolute;
    top: 64px;
    right: 25px;

    background: linear-gradient(100deg, #fbb900 5%, #ffeb00 10%, #fbb900 15%);
    background-size: 400%;
    -webkit-mask-image: url('images/final-score.svg');
    mask-image: url('images/final-score.svg');
    -webkit-mask-size: 100% 100%;
    mask-size: 100% 100%;
    animation: shine 3s linear infinite;
  }

  .logo--mobile {
    width: 45%;
    height: 40%;
    right: 3.5%;
    top: 5%;
    background-size: 445%;
  }

  @keyframes shine {
    from {
      background-position: -272px;
    }
    
    to {
      background-position: 544px;
    }
  }
  @-webkit-keyframes shine {
    from {
      background-position: -272px;
    }
    
    to {
      background-position: 544px;
    }
  }

  .dave {
    width: 100%;
    height: 666px;
    position: absolute;
    bottom: -100px;
    right: -40px;
    animation: scale 8s ease-out infinite;
    transform-origin: bottom right;
  }
  .dave img {
    max-width: 100%;
    filter: grayscale(20%);
  }

  @keyframes scale {
    from {
      transform: scale(0.95,0.95)
    }
    to {
      transform: scale(1.05, 1.05)
    }
  }
  @-webkit-keyframes scale {
    from {
      -webkit-transform: scale(0.95,0.95)
    }
    to {
      -webkit-transform: scale(1.05, 1.05)
    }
  }

  .mobile--height {
    height: 416px;
  }

  .fallback img {
    max-width: 100%;
    height: auto;
  }

  p {
    padding: 0px 20px;
  }
</style>
