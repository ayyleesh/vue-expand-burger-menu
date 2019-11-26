<template>
  <header class="header" v-bind:class="[isPanelOpen? open : '']" @click="closePanel">
    <div class="top-menu">
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
      open: "panel-open"
    };
  },
  methods: {
    closePanel: mutations.toggleNav()
  },
  computed: {
    isPanelOpen() {
      return store.isNavOpen;
    }
  }
};
</script>

<style scoped>
header.header {
  background-image: url("http://placehold.it/1000x1000");
  background-size: cover;
  background-position: center;
}
.top-menu {
  display: flex;
  flex-wrap: wrap;
  align-items: center;
  justify-content: space-between;
}
.top-menu > *:last-child {
  flex: 0 0 100%;
}

@media screen and (max-width: 768px) {
  header.header {
    background-image: none;
    background-color: skyblue;
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
