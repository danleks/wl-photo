<template>
  <div id="app">
    <div :class="[modal ? blured : '', mainWrapper]">
      <app-hero>
        <slot name="arrowDown"></slot>
      </app-hero>
      <app-menu
        :menuActive="menuActive"
        @close-menu="closeMenu()"
      ></app-menu>
      <app-about></app-about>
      <app-gallery
      :gallery="gallery"
      @show-modal="showModal"
      ></app-gallery>
    </div>
    <app-modal
      v-if="modal"
      :modalImg="modalImg"
      :sortedImg="sortedImg"
      :gallery="gallery"
      @close-modal="modal = false"
      ></app-modal>
  </div>
</template>

<script>
import Hero from './components/Hero.vue';
import Claim from './components/Claim.vue';
import Menu from './components/Menu.vue';
import About from './components/About.vue';
import Gallery from './components/Gallery.vue';
import Modal from './components/Modal.vue';


export default {
  name: 'app',
  components: {
    'app-hero': Hero,
    'app-claim': Claim,
    'app-menu': Menu,
    'app-about': About,
    'app-gallery': Gallery,
    'app-modal': Modal,
  },
  data() {
    return {
      menuActive: false,
      x: 0,
      modal: false,
      modalImg: {},
      sortedImg: [],
      mainWrapper: 'mainWrapper',
      blured: 'mainWrapper--blured',
      gallery: [
        {
          id: 0,
          url: require('./assets/gallery-1.jpg'),
          caption: '',
          label: 'nature',
        },
        {
          id: 1,
          url: require('./assets/gallery-2.jpg'),
          caption: '',
          label: 'nature',
        },
        {
          id: 2,
          url: require('./assets/gallery-3.jpg'),
          caption: '',
          label: 'building',
        },
        {
          id: 3,
          url: require('./assets/gallery-4.jpg'),
          caption: '',
          label: 'building',
        },
        {
          id: 4,
          url: require('./assets/gallery-5.jpg'),
          caption: '',
          label: 'nature',

        },
        {
          id: 5,
          url: require('./assets/gallery-6.jpg'),
          caption: '',
          label: 'cars',

        },
        {
          id: 6,
          url: require('./assets/gallery-7.jpg'),
          caption: '',
          label: 'buildings',
        },
        {
          id: 7,
          url: require('./assets/gallery-8.jpg'),
          caption: '',
          label: 'animals',
        },
      ]
    }
  },

  methods: {
    closeMenu() {
      if (this.menuActive === false) {
        this.menuActive = true;
      } else {
        this.menuActive = false;
      }
    },

    showModal(img, sortedImg) {
      console.log(img);
      this.modal = true;
      this.modalImg = img;
      this.sortedImg = sortedImg;
    }
  },

  mounted() {

  }
};
</script>

<style lang="scss">
@import url('https://fonts.googleapis.com/css?family=Cabin:100,400,400i,500i,700');
:root {
  --sectionGutter: 2rem;
  --mainLetterFontSize: 7.2rem;
  --headerFontsize: 2.4rem;
  --headerLetterSpacing: .2rem;
  --contentFontsize: 1.4rem;
  --contentLetterSpacing: .1rem;
}
html {
  box-sizing: border-box;
  scroll-behavior: smooth;
  font-size: 62.5%;
}

*, *:before, *:after {
  box-sizing: inherit;
  padding: 0;
  margin: 0;

  -webkit-tap-highlight-color: transparent;
}

#app {
  height: 100vh;
  font-family: 'Cabin', sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
}

.mainWrapper {
  position: relative;

  &--blured {
    filter: blur(3px);
  }
}
</style>
