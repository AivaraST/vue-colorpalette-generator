<template>
  <div id="app">
    <Header></Header>
    <router-view></router-view>
    <Footer></Footer>
  </div>
</template>

<script>
import Header from '@/components/Shared/Header.vue';
import Footer from '@/components/Shared/Footer.vue';

export default {
  name: 'App',
  components: {
    Header,
    Footer,
  },
};
</script>

<style lang="scss">
// Resets
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

a, a:hover, a:active, a:focus {
    color: black;
    text-decoration: none;
}

// Main styling
body {
  background: #E8ECF3;
  font-family: 'Montserrat', sans-serif;
  font-size: 16px;
  color: #fefefe
}

// Container
.container {
  max-width: 1200px;
  padding: 0 50px;
  margin: 0 auto;
}
</style>
