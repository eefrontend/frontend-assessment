<template>
  <div id="app">
    <responsive-data-display :data="sectionsData" />
  </div>
</template>

<script>
import ResponsiveDataDisplay from "./components/ResponsiveDataDisplay.vue";
import sectionsData from "./data.json";

export default {
  name: "App",
  components: {
    ResponsiveDataDisplay,
  },
  data() {
    return { sectionsData };
  },
};
</script>

<style lang="scss">
@import url("https://fonts.googleapis.com/css2?family=Poppins:wght@300;400;600&display=swap");

html,
body {
  padding: 0;
  margin: 0;
}

html {
  font-size: $font-size-base;
}
@media (min-width: $media-desktop-l) {
  html {
    font-size: $font-size-base-desktop-l;
  }
}
@media (min-width: $media-desktop-xl) {
  html {
    font-size: $font-size-base-desktop-xl;
  }
}

body {
  font-family: $font-primary;
  color: $color-black;
}

* {
  box-sizing: border-box;
}

h1,
h2,
p {
  margin: 0;
}

#app {
  padding: 1.5rem;
}
</style>
