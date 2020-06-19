<template>
  <div id="app">
    <Navbar />
    <Sidebar />
  </div>
</template>

<script>
import Navbar from './components/Navbar';
import Sidebar from './components/Sidebar';

export default {
  name: 'App',

  components: {
    Navbar,
    Sidebar
  },

  data: () => ({
    //
  }),
};
</script>

<style lang="scss">
body {
  margin: 0;
}

#app {
  height: 100vh;
  padding: 28px 100px 50px 100px;
  font-size: 32px;

  @media screen and (max-width: 1919px) and (max-height: 1080px) {
    font-size: 24px;
  }
}

p, h1, h2, h3, div, span, label {
  font-family: Calibri;
}
</style>
