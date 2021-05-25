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

<style>
@import url("https://fonts.googleapis.com/css2?family=Poppins:wght@300;400;600&display=swap");

html,
body {
  padding: 0;
  margin: 0;
}

html {
  font-size: 16px;
}
@media (min-width: 1800px) {
  html {
    font-size: 19px;
  }
}
@media (min-width: 2000px) {
  html {
    font-size: 21px;
  }
}

body {
  font-family: "Poppins", sans-serif;
}

* {
  box-sizing: border-box;
}

h1 {
  margin: 0;
}

#app {
  padding: 1.5rem;
}
</style>
