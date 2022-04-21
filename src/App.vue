<template>
  <TheHeader title="Learning Resources"></TheHeader>
  <TheResources></TheResources>
</template>

<script>

import TheHeader from "./components/layouts/TheHeader";
import TheResources from "./components/LearningResources/TheResources";

export default {
  name: "App.vue",
  components: { TheHeader, TheResources },
  data() {
    return {
    }
  }
}
</script>

<style>

@import url('https://fonts.googleapis.com/css2?family=Roboto:wght@400;700&display=swap');

* {
  box-sizing: border-box;
}

html {
  font-family: 'Roboto', sans-serif;
}

body {
  margin: 0;
}

</style>