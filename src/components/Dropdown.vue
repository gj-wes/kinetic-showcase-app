<template>
  <div>
    <mail-header v-if="mobile"></mail-header>
    <section class="kinetic" v-if="kinetic">
      <div class="menu__header">
        <div class="menu__button" @click="menuOpen = !menuOpen">
          <span class="slice"></span>
          <span class="slice"></span>
          <span class="slice"></span>
        </div>
      </div>
      <div class="menu" :class="{'menu--open':menuOpen}">
        <div class="menu__item">Item 1</div>
        <div class="menu__item">Item 2</div>
        <div class="menu__item">Item 3</div>
        <div class="menu__item">Item 4</div>
      </div>
    </section>
    <section class="fallback" v-else>
      <div class="menu__item">Item 1</div>
      <div class="menu__item">Item 2</div>
      <div class="menu__item">Item 3</div>
      <div class="menu__item">Item 4</div>
    </section>
    <section class="hero">
      <img src="https://placehold.it/600x300?text=Hero" alt="">
      <h1>Dropdown Menu</h1>
      <p>
        This menu looks best on <u>mobile</u> view.
        <br><br>
        Lorem ipsum dolor sit amet consectetur adipisicing elit. Ducimus delectus laudantium, laborum repellendus eum natus.
      </p>
    </section>
  </div>
</template>

<script>
import MailHeader from "./MailHeader.vue";
export default {
  name: 'Dropdown',
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
      menuOpen: false
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
  .menu__header {
    display: flex;
    justify-content: flex-end;
    padding: 10px;
  }
  .menu__button .slice {
    display: flex;
    flex-direction: column;
    width: 30px;
    height: 5px;
    border-radius: 2px;
    margin-bottom: 4px;
    background: linear-gradient(
    to right,
      rgba(247, 145, 2, 1) 0%,
      rgba(239, 45, 45, 1) 50%,
      rgba(24, 88, 226, 1) 100%
    );
  }
  .menu__button .slice:last-child {
    margin-bottom: 0;
  }

  .menu {
    overflow: hidden;
    max-height: 0;
    transition: all 1s ease-in-out;
  }

  .menu--open {
    max-height: 400px;
  }

  .kinetic .menu__item {
    padding: 10px;
    border-bottom: 1px solid slateblue;
  }
  .kinetic .menu__item:first-child {
    border-top: 1px solid slateblue;
  }


  /* FALLBACK */
  .fallback {
    display: flex;
    justify-content: space-around;
    flex-wrap: wrap;
  }

  .fallback .menu__item {
    flex: 1 1 150px;
    padding: 10px 0px;
  }

  img {
    max-width: 100%;
    height: auto;
  }
</style>