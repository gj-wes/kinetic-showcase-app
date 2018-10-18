<template>
  <div>
    <mail-header v-if="mobile"></mail-header>
    <section>
      <h1>Accordion Content</h1>
      <p>
        Lorem ipsum dolor sit amet consectetur adipisicing elit. Delectus, repellat!
      </p>
    </section>
    <section class="accordion" v-if="kinetic">
      <div class="accordion__pod" @click="pod1Open = !pod1Open">
        <h3>Pod 1 <div class="pod__indicator">+</div></h3>
        <p class="pod__content" :class="{'pod__content--open':pod1Open}">Lorem ipsum dolor sit amet consectetur adipisicing elit. Eveniet iusto ducimus pariatur quasi quibusdam modi, ad excepturi corrupti expedita deleniti dolore ea laboriosam consectetur nihil!</p>
      </div>
      <div class="accordion__pod" @click="pod2Open = !pod2Open">
        <h3>Pod 2 <div class="pod__indicator">+</div></h3>
        <p class="pod__content" :class="{'pod__content--open':pod2Open}">Lorem ipsum dolor sit amet consectetur adipisicing elit. Eveniet iusto ducimus pariatur quasi quibusdam modi, ad excepturi corrupti expedita deleniti dolore ea laboriosam consectetur nihil!</p>
      </div>
      <div class="accordion__pod" @click="pod3Open = !pod3Open">
        <h3>Pod 3 <div class="pod__indicator">+</div></h3>
        <p class="pod__content" :class="{'pod__content--open':pod3Open}">Lorem ipsum dolor sit amet consectetur adipisicing elit. Eveniet iusto ducimus pariatur quasi quibusdam modi, ad excepturi corrupti expedita deleniti dolore ea laboriosam consectetur nihil!</p>
      </div>
    </section>
    <section class="fallback" v-else>
      <h3>Pod 1</h3>
      <p>Lorem ipsum dolor sit amet consectetur adipisicing elit. Eveniet iusto ducimus pariatur quasi quibusdam modi, ad excepturi corrupti expedita deleniti dolore ea laboriosam consectetur nihil!</p>
      <h3>Pod 2</h3>
      <p>Lorem ipsum dolor sit amet consectetur adipisicing elit. Eveniet iusto ducimus pariatur quasi quibusdam modi, ad excepturi corrupti expedita deleniti dolore ea laboriosam consectetur nihil!</p>
      <h3>Pod 3</h3>
      <p>Lorem ipsum dolor sit amet consectetur adipisicing elit. Eveniet iusto ducimus pariatur quasi quibusdam modi, ad excepturi corrupti expedita deleniti dolore ea laboriosam consectetur nihil!</p>
    </section>
  </div>
</template>

<script>
import MailHeader from "./MailHeader.vue";
export default {
  name: 'Accordion',
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
      pod1Open: false,
      pod2Open: false,
      pod3Open: false
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
  .accordion__pod {
    padding: 10px 20px;
    box-shadow: 0px 2px 14px rgba(0,0,0,0.4);
    border-radius: 8px;
    margin: 0 10px 15px 10px;
  }

  .accordion__pod h3 {
    margin: 0;
    display: flex;
    justify-content: space-between;
    align-items: center;
  }

  .pod__content {
    text-align: left;
    max-height: 0;
    overflow: hidden;
    transition: all 0.6s ease-in-out;
    margin: 0;
  }

  .pod__content--open {
    margin: 1em 0; 
    max-height: 300px;
  }

  .pod__indicator {
    font-size: 2em;
    line-height: 1;
  }

</style>