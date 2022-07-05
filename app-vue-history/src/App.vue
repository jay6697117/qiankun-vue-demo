<template>
  <div id="app">
    <div id="nav">
      <router-link to="/">Home</router-link>
      |
      <router-link to="/about">About</router-link>
    </div>
    <div style="color: red;font-weight: bold;">commonData:{{commonData}}</div>
    <router-view />
  </div>
</template>

<script>
export default {
  data() {
    return {
      isQiankun: window.__POWERED_BY_QIANKUN__
    };
  },
  computed: {
    commonData() {
      return this.isQiankun ? this.$root.parentVuex.state.commonData : '';
    }
  },
  mounted() {
    console.log('this.$root.parentVuex', this.$root.parentVuex);
  }
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

#nav {
  padding: 30px;
}

#nav a {
  font-weight: bold;
  color: #2c3e50;
}

#nav a.router-link-exact-active {
  color: #42b983;
}
</style>
