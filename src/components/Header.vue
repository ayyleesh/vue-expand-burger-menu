<template>
  <header
    class="header"
    v-bind:class="[isPanelOpen? open : '']"
    @click="closePanel"
    @scroll="handleScroll"
  >
    <div class="top-menu" v-bind:class="{sticky : isSticky }">
      <Logo/>
      <Burger/>
      <transition name="slide">
        <Menu v-bind:class="[isPanelOpen? '' : noDisplay]"/>
      </transition>
    </div>
  </header>
</template>

<script>
import Logo from "./Logo";
import Burger from "./Burger";
import Menu from "./Menu";
import { store, mutations } from "@/store.js";
export default {
  name: "Header",
  components: { Logo, Burger, Menu },
  data() {
    return {
      noDisplay: "no-display",
      open: "panel-open",
      isSticky: true
    };
  },
  methods: {
    closePanel: mutations.toggleNav(),
    handleScroll: function(e) {
      this.isSticky = window.scrollY > window.innerHeight / 2;
    }
  },
  computed: {
    isPanelOpen() {
      return store.isNavOpen;
    }
  },
  created() {
    window.addEventListener("scroll", this.handleScroll);
  }
};
</script>

<style scoped>
header.header {
  background-image: url("http://placehold.it/1000x1000");
  background-size: cover;
  background-position: center;
  height: 90vh;
}
.top-menu {
  display: flex;
  flex-wrap: wrap;
  align-items: center;
  justify-content: space-between;
  width: 100%;
}
.top-menu > *:last-child {
  flex: 0 0 100%;
}
.sticky {
  position: fixed;
  background: white;
  z-index: 2;
}

@media screen and (max-width: 768px) {
  header.header {
    background-image: none;
    background-color: skyblue;
    height: initial;
  }
  .panel-open {
    height: 100%;
    width: 100%;
    position: fixed;
  }
  .no-display {
    display: none;
  }
}
</style>
