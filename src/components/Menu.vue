<template>
  <ul>
    <li>Menu 1</li>
    <li>Menu 2</li>
    <li>Menu 3</li>
    <li>Menu 4</li>
    <li>Menu 5</li>
  </ul>
</template>

<script>
export default {
  name: "Menu"
};
</script>

<style scoped>
ul {
  display: flex;
}
li {
  list-style: none;
  padding: 1em;
}

@media only screen and (max-width: 768px) {
  ul {
    display: block;
  }
}
</style>
