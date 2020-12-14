<template>
  <the-header title="Remerber Me"></the-header>
  <the-resources></the-resources>
  <!-- <StoredResources :resources="storedResources"></StoredResources> -->
</template>

<script>
import TheResources from './components/LearningResources/TheResources';
// import StoredResources from './components/LearningResources/StoredResources';
import TheHeader from './components/layouts/TheHeader';
export default {
  components: {
    // StoredResources,
    TheHeader,
    TheResources
  }
};
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
