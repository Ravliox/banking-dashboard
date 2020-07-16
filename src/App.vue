<template>
  <div id="app">
    <Navbar />
    <div class="content">
      <Sidebar />
      <SidebarMobile :sidebar="mobileSidebar" @retractSidebar="retract()"/>
      <Dashboard />
      <div class="mobile-nav-menu">
        <div>
          <v-btn icon>
            <v-icon>mdi-bell</v-icon>
            <div class="notification-number">3</div>
          </v-btn>
          <p> Notifications </p>
        </div>
        <div>
          <v-btn icon><v-icon>mdi-home-outline</v-icon></v-btn>
          <p> Home </p>
        </div>
        <div>
          <v-btn icon @click="expandSidebar()"><v-icon>mdi-menu</v-icon></v-btn>
          <p> Menu </p>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import Navbar from './components/Navbar';
import Sidebar from './components/Sidebar';
import SidebarMobile from './components/SidebarMobile';
import Dashboard from './pages/Dashboard';

export default {
  name: 'App',

  components: {
    Navbar,
    Sidebar,
    SidebarMobile,
    Dashboard
  },

  data: () => ({
    mobileSidebar:  {
      hidden: true,
      rendered: false
    }
  }),
  methods: {
    retract() {      
      this.mobileSidebar.hidden = true;
      setTimeout(() => { 
        this.mobileSidebar.rendered = false 
      }, 200)
    },
    expandSidebar() {
      this.mobileSidebar = new Object({hidden: false, rendered: true})
    }
  }
};
</script>

<style lang="scss">
body {
  margin: 0;
}

html {
  font-size: 24px;

  @media screen and (max-width: 1919px) and (max-height: 1080px) {
    font-size: 22px;
  }

  @media screen and (min-width: 1000px) and (max-height: 700px) {
    font-size: 18px;
  }
}

#app {
  height: 100vh;
  padding: 0.75em 3.12em;
  padding-bottom: 1.2em;
  display: flex;
  flex-direction: column;
  width: 100vw;
}

.content {
  width: 100%;
  flex: 1 0 auto;
  display: flex;
}

p, h1, h2, h3, div, span, label {
  font-family: Calibri;
}

.mobile-nav-menu {
  display: none;
}

@media screen and (max-width: 800px) {
  #app {
    padding: 5px 8px;
    overflow: hidden;
    height: 100vh;
  }

  html {
    font-size: 18px;
  }

  .content {
    overflow: hidden;
    flex: unset;
    padding-bottom: 100px;
  }

  .mobile-nav-menu {
    display: flex;
    position: fixed;
    justify-content: space-between;
    height: 55px;
    width: 100vw;
    padding: 0 10px;
    background-color: #fff;
    bottom: 0;
    left: 0;
    box-shadow: 0px -7px 9px 0px rgba(0,0,0, 0.2);

    & > div {
      width: 20%;
      display: flex;
      flex-direction: column;
      align-items: center;

      button {
        position: relative;
      }

      p {
        font-size: 12px;
      }
    }

    .notification-number {
      position: absolute;
      left: 20px;
      top: -3px;

    }
  }
}
</style>
