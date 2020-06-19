<template>
  <div id="navbar">
    <p class="logo">BFS<sup>4e</sup></p>
    <div class ="right">
        <v-text-field class="search" label="Search">
            <v-icon slot="append" color="red">mdi-magnify</v-icon>
        </v-text-field>
        <v-icon class="notification-icon" size="28">mdi-bell</v-icon>
        <div class="notification-number">3</div>
    </div>
  </div>
</template>

<script>
export default {

}
</script>

<style lang="scss">
#navbar {
    display: flex;
    width: 100%;
    height: 56px;
    justify-content: space-between;
}

.logo {
    font-size: 48px;
    margin: 0;
    font-weight: bold;

    sup {
        color: #045E07;
        font-size: 28px;
    }
}

.search {
    width: 220px;
    flex: unset !important;
    margin-right: 10px;
}

.right {
    display: flex;
}

.notification-icon {
    position: relative;
    top: 5px;
}

.notification-number {
    position: relative;
    height: 19px;
    width: 15px;
    font-size: 15px;
    background-color: #045E07;
    border: 1px solid #fff;
    color: #fff;
    border-radius: 3px;
    display: flex;
    justify-content: center;
    align-items: center;
    left: -12px;
    top: 15px;
}
</style>