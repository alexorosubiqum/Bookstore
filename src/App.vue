<template>
  <div id="app">
    <Bookstore />
  </div>
</template>

<script>
import Bookstore from "./components/Bookstore.vue";
export default {
  name: "App",
  components: {
    Bookstore
  }
};
</script>

<style>
body {
  background-image: url(./assets/bgBooks.jpg);
  background-attachment: fixed;
  background-size: cover;
}

body h1,
h3 {
  text-transform: uppercase;
  color: white;
}

body p {
  color: white;
}
</style>
