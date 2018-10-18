<template>
  <div id="app">
    <header>
      Kinetic showcase
    </header>
    <main class="display-area">
      <aside>
        <h2>Modules</h2>
        <!-- Dynamically create buttons against data array, add click event and change button display text -->
        <button v-for="(component, i) in componentsArray" @click="swapComponent(component)" :key="i">{{ component }}</button>
      </aside>
      <section class="preview-area">
        <div class="preview-controls" v-if="!startMessage">
          <button @click="toggleView" v-text="viewportButton"></button>
          <button @click="toggleFallback" v-text="stateButton"></button>
        </div>
        <!-- Message visible before any component loaded -->
        <p v-if="startMessage">Select a component on the left to load the preview</p>

        <!-- CSS device frame for mobile views -->
        <div :class="[{'marvel-device': toggleMobileView}, deviceViewType, 'silver']">
          <div :class="{'top-bar': toggleMobileView}"></div>
          <div :class="{'sleep': toggleMobileView}"></div>
          <div :class="{'volume': toggleMobileView}"></div>
          <div :class="{'camera': toggleMobileView}"></div>
          <div :class="{'sensor': toggleMobileView}"></div>
          <div :class="{'speaker': toggleMobileView}"></div>
          <div :class="{'screen': toggleMobileView}">

            <div v-if="visibleComponent" class="kinetic-container" :class="{'kinetic-container--is-mobile': toggleMobileView, 'kinetic-container--border': !toggleMobileView}">
              <!-- Kinetic component loads here - bound to data property -->
              <div :is="visibleComponent" :is-kinetic-view="toggleKinetic" :is-mobile="toggleMobileView"></div>
            </div>

          </div>
          <div :class="{'home': toggleMobileView}"></div>
          <div :class="{'bottom-bar': toggleMobileView}"></div>
        </div>

      </section>
    </main>
  </div>
</template>

<script>
  import CarouselSlider from "./components/CarouselSlider.vue";
  import CarouselButtons from "./components/CarouselButtons.vue";
  import Accordion from "./components/Accordion.vue";
  import Dropdown from "./components/Dropdown.vue";
  import TapAndFlip from "./components/TapAndFlip.vue";
  import Hotspot from "./components/Hotspot.vue";
  import CSSAnim from "./components/CSSAnim.vue"

  export default {
    name: "app",
    components: {
      "Slider Carousel": CarouselSlider,
      "Button Carousel": CarouselButtons,
      "Accordion Content": Accordion,
      "Dropdown Menu": Dropdown,
      "Tap and Flip": TapAndFlip,
      "Hotspots": Hotspot,
      "CSS Animations": CSSAnim
    },
    data() {
      return {
        viewportButton: '',
        stateButton: '',
        startMessage: true,
        visibleComponent: null,
        toggleMobileView: null,
        toggleKinetic: null,
        componentsArray: ["Slider Carousel", "Button Carousel", "Accordion Content","Dropdown Menu","Tap and Flip","Hotspots", "CSS Animations"],
        deviceViewType: 'iphone8'
      };
    },
    methods: {
      swapComponent(component) {
        // hide start message
        this.startMessage = false;
        // set kinetic view to true by default on loading new component
        this.toggleKinetic = true;
        // set state button text
        this.stateButton = 'Switch to Fallback';
        // set desktop view
        this.toggleMobileView = false;
        // set desktop view button
        this.viewportButton = 'Switch to Mobile';
        // change visible component
        this.visibleComponent = component;
      },
      buttonDisplayName(name) {
        // chops off kinetic-
        return name.slice(8);
      },
      toggleView() {
        // switch between desktop and mobile sizes for container and change button text
        this.toggleMobileView = !this.toggleMobileView;
        this.toggleMobileView ? this.viewportButton = 'Switch to Desktop' : this.viewportButton = 'Switch to Mobile';
      },
      toggleFallback() {
        // toggle kinetic and fallback views in component and change button text
        this.toggleKinetic = !this.toggleKinetic;
        this.toggleKinetic ? this.stateButton = 'Switch to Fallback' : this.stateButton = 'Switch to Kinetic';
      }
    }
  };
</script>

<style>
@import url('./assets/devices.min.css');

body {
  margin: 0;
  padding: 0;
  font-size: 16px;
  line-height: 1.1;
}

@font-face {
  font-family: sky_textregular;
  src: url("https://static.skyassets.com/assets/fonts/sky-regular.woff");
}

#app {
  font-family: "sky_textregular", Arial, Helvetica, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

header {
  padding: 1rem;
  font-size: 2rem;
  text-align: center;
  color: white;
  background: linear-gradient(
    to right,
    rgba(247, 145, 2, 1) 0%,
    rgba(239, 45, 45, 1) 50%,
    rgba(24, 88, 226, 1) 100%
  );
}

.display-area {
  display: grid;
  height: calc(100vh - 67px);
  grid-template-columns: 1fr 3fr;
}

aside {
  padding: 20px;
  border-right: 1px solid lightsalmon;
}

aside h2 {
  margin-top: 0;
}

aside button {
  width: 100%;
  padding: 10px 0px;
  margin-bottom: 20px;
  border: 1px solid grey;
  border-radius: 5px;
}

.preview-controls {
  display: flex;
  justify-content: space-around;
  align-items: center;
  padding: 20px;
  margin-bottom: 20px;
  border-bottom: 1px solid lightsalmon;
}

.preview-controls button {
  padding: 10px 15px;
  border: 1px solid grey;
  border-radius: 5px;
}

.kinetic-container {
  width: 600px;
  margin: 0 auto;
  transition: width 0.2s linear;
}

.kinetic-container--border {
  border: 1px solid lightslategray;
}

.kinetic-container--is-mobile {
  overflow-y: scroll;
  /* iPhone6 screen size */
  width: 375px;
  height: 667px;
}

</style>
