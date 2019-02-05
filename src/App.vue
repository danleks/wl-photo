<template>
  <div id="app">
    <div class="spinnerWrapper" v-if="spinner">
      <div class="spinnerWrapper__item"></div>
      <div class="spinnerWrapper__text"><span>Loading</span></div>
    </div>
    <div v-if="!spinner" :class="[modal ? blured : '', mainWrapper]">
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
      spinner: true,
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
    },

    loadSpinner() {
      setTimeout(()=>{
        this.spinner = false;
      }, 1200)
    }
  },

  mounted() {
    this.loadSpinner();
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

.spinnerWrapper {
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);

  width: 8rem;
  height: 6rem;


  &__item {
    position: absolute;
    top: 0;
    left: 50%;
    transform: translate(-50%);
    width: 3rem;
    height: 3rem;
    border-radius: 50%;
    background-color: #ccc;

    animation: spinner .8s infinite;
  }

  &__text {
    position: absolute;
    bottom: 0;
    left: 50%;
    transform: translate(-50%);
    font-size: 1.2rem;
    text-transform: uppercase;
    letter-spacing: 2px;
  }
}

@keyframes spinner {
  0% {width: 3rem; height: 3rem;}
  50% {width: 4rem; height: 4rem;}
  100% {width: 3rem; height: 3rem;}
}
</style>
