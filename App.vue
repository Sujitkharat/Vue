<template>
  <!-- <img alt="Vue logo" src="./assets/logo.png"> -->
  <div>
    <router-link to="/"></router-link>
    <router-link to="/about"></router-link>

    <router-view></router-view>
  </div>
</template>

<script>

export default {
  name: 'App',
  components: {

  }
}
</script>

<style>
#app {
background-color:rgba(254, 255, 212, 0.664);
}
</style>
