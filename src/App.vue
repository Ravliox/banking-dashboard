<template>
  <div id="app">
    <Navbar />
    <div class="content">
      <Sidebar />
      <Dashboard />
    </div>
  </div>
</template>

<script>
import Navbar from './components/Navbar';
import Sidebar from './components/Sidebar';
import Dashboard from './pages/Dashboard';

export default {
  name: 'App',

  components: {
    Navbar,
    Sidebar,
    Dashboard
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
  display: flex;
  flex-direction: column;

  @media screen and (max-width: 1919px) and (max-height: 1080px) {
    font-size: 24px;
  }

  @media screen and (min-width: 1000px) and (max-height: 700px) {
    font-size: 18px;
  }
}

.content {
  width: 100%;
  flex: 1 0 auto;
  display: flex;
}

p, h1, h2, h3, div, span, label {
  font-family: Calibri;
}
</style>
