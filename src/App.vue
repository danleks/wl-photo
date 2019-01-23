<template>
  <div id="app">
    <div class="mainWrapper">
      <app-hero>
        <slot name="arrowDown"></slot>
      </app-hero>
      <app-menu
        :menuActive="menuActive"
        @close-menu="closeMenu()"
      ></app-menu>
      <app-about></app-about>
    </div>
  </div>
</template>

<script>
import Hero from './components/Hero.vue';
import Claim from './components/Claim.vue';
import Menu from './components/Menu.vue';
import About from './components/About.vue';



export default {
  name: 'app',
  components: {
    'app-hero': Hero,
    'app-claim': Claim,
    'app-menu': Menu,
    'app-about': About,
  },
  data() {
    return {
      menuActive: false,
      x: 0,
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
  },

  mounted() {

  }
};
</script>

<style lang="scss">
@import url('https://fonts.googleapis.com/css?family=Cabin:100,400,400i,500i,700');
html {
  box-sizing: border-box;
  scroll-behavior: smooth;
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
}
</style>
