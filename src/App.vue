<template>
  <div id="app">
    <header>
      Kinetic showcase
    </header>
    <main class="display-area">
      <aside>
        <h2>Modules</h2>
        <!-- Dynamically create buttons against data array, add click event and change button display text -->
        <button v-for="(component, i) in componentsArray" @click="swapComponent(component)" :key="i" class="module-select-btn" :class="{'module-select-btn__selected': component === visibleComponent}">{{ componentDisplayName(component) }}</button>
      </aside>
      <section class="preview-area">
        <transition name="fade" mode="out-in">
        <h2 v-if="!startMessage" :key="visibleComponent">
          {{ componentDisplayName(visibleComponent) }}
        </h2>
        </transition>
        <div class="preview-controls" v-if="!startMessage">
          <button @click="toggleView" v-text="viewportButton" class="module-select-btn module-select-btn--preview"></button>
          <button @click="toggleFallback" v-text="stateButton" class="module-select-btn module-select-btn--preview"></button>
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
            
            <transition name="fade" mode="out-in">
            <div v-if="visibleComponent" class="kinetic-container" :class="{'kinetic-container--is-mobile': toggleMobileView, 'kinetic-container--border': !toggleMobileView}">
              <!-- Kinetic component loads here - bound to data property -->
              <transition name="fade" mode="out-in">
                <div :is="visibleComponent" :is-kinetic-view="toggleKinetic" :is-mobile="toggleMobileView"></div>
              </transition>
            </div>
            </transition>

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
import CSSAnim from "./components/CSSAnim.vue";

export default {
  name: "app",
  components: {
    "Slider-Carousel": CarouselSlider,
    "Button-Carousel": CarouselButtons,
    "Accordion-Content": Accordion,
    "Dropdown-Menu": Dropdown,
    "Tap-and-Flip": TapAndFlip,
    Hotspots: Hotspot,
    "CSS-Animations": CSSAnim
  },
  data() {
    return {
      viewportButton: "",
      stateButton: "",
      startMessage: true,
      visibleComponent: null,
      toggleMobileView: null,
      toggleKinetic: null,
      componentsArray: [
        "Slider-Carousel",
        "Button-Carousel",
        "Accordion-Content",
        "Dropdown-Menu",
        "Tap-and-Flip",
        "Hotspots",
        "CSS-Animations"
      ],
      deviceViewType: "iphone8"
    };
  },
  methods: {
    swapComponent(component) {
      // hide start message
      this.startMessage = false;
      // set kinetic view to true by default on loading new component
      this.toggleKinetic = true;
      // set state button text
      this.stateButton = "Switch to Fallback";
      // set desktop view
      this.toggleMobileView = false;
      // set desktop view button
      this.viewportButton = "Switch to Mobile";
      // change visible component
      this.visibleComponent = component;
    },
    componentDisplayName(name) {
      // remove dashes from component names
      return name.replace(/-/g, " ");
    },
    toggleView() {
      // switch between desktop and mobile sizes for container and change button text
      this.toggleMobileView = !this.toggleMobileView;
      this.toggleMobileView
        ? (this.viewportButton = "Switch to Desktop")
        : (this.viewportButton = "Switch to Mobile");
    },
    toggleFallback() {
      // toggle kinetic and fallback views in component and change button text
      this.toggleKinetic = !this.toggleKinetic;
      this.toggleKinetic
        ? (this.stateButton = "Switch to Fallback")
        : (this.stateButton = "Switch to Kinetic");
    }
  }
};
</script>

<style>
@import url("./assets/devices.min.css");

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
    rgb(255, 158, 0) 0%, 
    rgb(255, 0, 0) 25%, 
    rgb(181, 0, 125) 50%, 
    rgb(33, 66, 156) 75%, 
    rgb(0, 113, 255) 100%)
}

.display-area {
  display: grid;
  height: calc(100vh - 67px);
  grid-template-columns: minmax(auto, 400px) 1fr;
}

aside {
  padding: 20px;
  border-right: 1px solid lightsalmon;
}

aside h2 {
  margin-top: 0;
}

.module-select-btn {
  width: 100%;
  -moz-box-align: center;
  align-items: center;
  border-radius: 4px;
  border: 1px solid transparent;
  cursor: pointer;
  display: inline-flex;
  flex-shrink: 0;
  font-weight: bold;
  -moz-box-pack: center;
  justify-content: center;
  line-height: 24px;
  outline: currentcolor none medium;
  position: relative;
  text-align: center;
  transition-duration: 300ms;
  transition-property: background, color, box-shadow;
  transition-timing-function: ease;
  background-color: rgb(0, 15, 245);
  background-image: linear-gradient(-1deg, transparent 49%, rgba(255, 255, 255, 0.15) 50%, rgba(225, 225, 225, 0));
  color: rgb(255, 255, 255);
  font-size: 18px;
  font-family: inherit;
  padding: 8px 16px;
  margin-bottom: 10px;
}
.module-select-btn::after {
  content: "";
  border: 2px solid rgb(0, 160, 255);
  border-radius: 8px;
  inset: -5px;
  opacity: 0;
  pointer-events: none;
  position: absolute;
  transition: opacity 150ms linear 0s;
}
.module-select-btn:hover {
  background-color: rgb(0, 15, 190);
}
.module-select-btn__selected,
.module-select-btn__selected:hover {
  background-color: rgb(0, 15, 190);
}

.module-select-btn--preview {
  width: auto;
}

.preview-controls {
  display: flex;
  justify-content: space-around;
  align-items: center;
  padding: 0px 20px 20px 20px;
  margin-bottom: 20px;
  border-bottom: 1px solid lightsalmon;
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

.fade-enter-active,
.fade-leave-active {
  transition: opacity 0.1s linear;
}
.fade-enter,
.fade-leave-to {
  opacity: 0;
}
</style>
