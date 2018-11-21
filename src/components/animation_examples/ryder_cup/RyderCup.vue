<template>
  <div>
    <section class="kinetic" :class="{'mobile--height': mobile}" v-if="kinetic">
      <div class="kinetic-container">
        <div class="frame frame1">
          <div class="ryder-full"></div>
          <div class="text"></div>
        </div>
        <div class="frame frame2">
          <div class="players"></div>
          <div class="text"></div>
        </div>
        <div class="frame frame3">
          <div class="players"></div>
          <div class="text"></div>
        </div>
        <div class="frame frame4">
          <div class="bg-slide-left"></div>
          <div class="bg-slide-right"></div>
          <div class="ryder"></div>
          <div class="text"></div>
          <div class="logo"></div>
          <div class="copy">
            feel it all
          </div>
          <div class="sheen"></div>
        </div>
      </div>
    </section>
    <section class="fallback" v-else>
      <img src="./images/fallback-gif-desk.gif" alt="Believe in Blue">
    </section>
    <p >
      FirstName,
      <br><br>
      Get ready for golf’s greatest battle as Europe clashes clubs with USA for the 42nd Ryder Cup. Follow all the action from Le Golf National live, only on Sky&nbsp;Sports.
    </p>
  </div>
</template>
<script>
export default {
  name: "RyderCupAnimation",
  props: {
    isKineticView: Boolean,
    isMobile: Boolean
  },
  mounted() {
    this.kinetic = this.isKineticView;
    this.mobile = this.isMobile;
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
  .kinetic-container {
    display: block !important;
    width: 100%;
    height: 460px;
    overflow: hidden;

    position: relative;

    background-image: url('images/kinetic_background.jpg');
    background-size: 2300px 460px; /* 5:1 */
    background-position: 25% 0;

    animation: background-scroll 17s linear infinite;
  }

  @keyframes background-scroll {
    0% {
      background-position: 30% 0;
    }
    90% {
      background-position: 70% 0;
    }
    95% {
      background-position: 28% 0;
    } 100% {
      background-position: 30% 0;
    }
  }

  .frame {
    width: 100%;
    height: 460px;
    position: absolute;
    top: 0;
    left: 0;
  }

  .frame div {
    position: absolute;

    background-size: 100%;
    background-repeat: no-repeat;
  }
        
  /* FRAME 1 */
  .frame1 {
    animation: frame1fade 17s linear infinite;
  }
  @keyframes frame1fade {
    0%,22% {
      opacity: 1;
    }
    23%, 100% {
      opacity: 0;
    }
  }

  .frame1 .ryder-full {
    width: 320px;
    height: 202px;
    left: 50%;
    transform: translateX(-50%);
    top: 20px;

    background-image: url('images/hero-ryder-logo-full.png');
  }

  .frame1 .text {
    width: 320px;
    height: 150px;
    left: 50%;
    transform: translateX(-50%);

    bottom: 30px;
    background-image: url('images/frame1-text.png');

    animation: frame1text 17s linear infinite;
  }

  @keyframes frame1text {
    0%,10% {
      opacity: 0;
    }
    11%, 100% {
      opacity: 1;
    }
  }

  /* FRAME 2 */
  .frame2 {
    animation: frame2fade 17s linear infinite;
  }
  @keyframes frame2fade {
    0%,23% {
      opacity: 0;
    }
    24%,47% {
      opacity: 1;
    }
    48%, 100% {
      opacity: 0;
    }
  }
  .frame2 .players {
    width: 600px;
    height: 460px;
    bottom: -15px;

    background-image: url('images/frame2-players.png');
    animation: frame2players 17s cubic-bezier(0.14, 0.76, 0.68, 0.13) infinite;
  }
  @keyframes frame2players {
    0%, 23% {
      transform: translateX(100%);
    }
    51%, 100% {
      transform: translateX(-100%);
    }
  }

  .frame2 .text {
    width: 320px;
    height: 150px;
    left: 50%;
    transform: translateX(-50%);

    bottom: 30px;
    background-image: url('images/frame2-text.png');
    animation: frame2text 17s linear infinite;
  }

  @keyframes frame2text {
    0%,24% {
      opacity: 0;
    }
    25%,100% {
      opacity: 1;
    }
  }
        

  /* FRAME 3 */
  .frame3 {
    animation: frame3fade 17s linear infinite;
  }
  @keyframes frame3fade {
    0%,48% {
      opacity: 0;
    }
    49%,73% {
      opacity: 1;
    }
    74%, 100% {
      opacity: 0;
    }
  }
  .frame3 .players {
    width: 600px;
    height: 460px;

    background-image: url('images/frame3-players.png');
    animation: frame3players 17s cubic-bezier(0.07, 1.22, 0.63, 0.77) infinite;
  }
  @keyframes frame3players {
    0%, 50% {
      transform: translateX(-100%);
    }
    75%, 100% {
      transform: translateX(0);
    }
  }
  .frame3 .text {
    width: 320px;
    height: 150px;
    left: 50%;
    transform: translateX(-50%);

    bottom: 30px;
    background-image: url('images/frame3-text.png');
    animation: frame3text 17s linear infinite;
  }

  @keyframes frame3text {
    0%,49% {
      opacity: 0;
    }
    50%,100% {
      opacity: 1;
    }
  }

  /* FRAME 4 */
  .frame4 .bg-slide-left,
  .frame4 .bg-slide-right {
    background: #030c7e;
    background: linear-gradient(to bottom, #203ad5, #0e1153);

    width: 600px;
    height: 460px;
  }

  .frame4 .bg-slide-left {
    transform: translateX(-100%);
    animation: slideInLeft 17s ease-in infinite;
  }
  @keyframes slideInLeft {
    0%, 72%, 98%, 100% {
      transform: translateX(-100%)
    }
    74%, 96% {
      transform: translateX(-49%);
    }
  }

  .frame4 .bg-slide-right {
    transform: translateX(100%);
    animation: slideInRight 17s ease-in infinite;
  }
  @keyframes slideInRight {
    0%, 72%, 98%, 100% {
      transform: translateX(100%)
    }
    74%,96% {
      transform: translateX(49%);
    }
  }

  .frame4 .ryder {
    width: 140px;
    height: 134px;
    left: 50%;
    transform: translateX(-50%);
    top: 20px;
    opacity: 0;

    background-image: url('images/hero-ryder-logo-notext.png');
    animation: fadeIn 17s linear .1s infinite;
  }

  .frame4 .text {
    width: 320px;
    height: 150px;
    left: 50%;
    transform: translateX(-50%);
    opacity: 0;

    top: 185px;
    background-image: url('images/frame4-text.png');
    animation: fadeIn 17s linear .3s infinite;
  }
  .frame4 .logo {
    width: 190px;
    height: 40px;
    left: 50%;
    transform: translateX(-50%);
    opacity: 0;

    top: 315px;
    background-image: url('images/frame4-ss-logo.png');
    animation: fadeIn 17s linear .5s infinite;
  }

  .frame4 .copy {
    left: 50%;
    transform: translateX(-50%);
    opacity: 0;
    top: 385px;
    text-align: center;
    font-family: 'sky_textregular', Arial, Helvetica, sans-serif;
    color: white;
    font-size: 30px;
    line-height: 1;

    animation: fadeIn 17s linear .7s infinite;
  }
  @keyframes fadeIn {
    0%, 74%, 90%, 100% {
      opacity: 0;
    }
    76%, 88% {
      opacity: 1;
    }
  }
  .frame4 .sheen {
    width: 600px;
    height: 450px;
    left: 0;
    top: -100%;
    opacity: 0;

    background-image: url('images/sheen.png');
    background-position: bottom;
    background-size: cover;
    animation: sheen 17s ease-in infinite;
  }
  @keyframes sheen {

    0%, 70% {
      top: -100%;
      opacity: 1;
    }
    82% {
      top: 0;
      opacity: 1;
    }
    97%, 99%{
      top: 0;
      opacity: 0;
    }
    100% {
      top: -100%;
      opacity: 0;
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