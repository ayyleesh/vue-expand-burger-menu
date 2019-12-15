<template>
  <div id="app">
    <Header/>
    <Home/>
  </div>
</template>

<script>
import Header from "./components/Header";
import Home from "./pages/Home";

export default {
  name: "App",
  components: {
    Header,
    Home
  },
  data() {
    return {
      newClass: false,
      scrollPosition: 0
    };
  }
};
</script>

<style>
html,
body {
  height: 100%;
  margin: 0;
}
#app {
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin: 0;
  padding: 0;
}
.new-class {
  color: red;
  position: fixed;
}
</style>
