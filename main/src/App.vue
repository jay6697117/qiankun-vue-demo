<template>
  <div id="app">
    <header>
      <router-link to="/app-vue-hash/">app-vue-hash</router-link>
      <router-link to="/app-vue-history/">app-vue-history</router-link>
      <router-link to="/base">Base基座</router-link>
      <span style="color:red;" @click="changeParentState">主项目的数据：{{ commonData.parent }}，点击+1</span>
    </header>
    <div id="appContainer"></div>
    <router-view></router-view>
  </div>
</template>

<script>
export default {
  computed: {
    commonData() {
      return this.$store.state.commonData;
    }
  },
  methods: {
    changeParentState() {
      //vuex mutations
      let parent = this.commonData.parent || 0;
      parent += 1;
      this.$store.commit('setCommonData', { parent });
    }
  }
};
</script>

<style scoped>
#app {
  height: 100vh;
  text-align: center;
  position: relative;
}
header > a {
  margin: 0 20px;
}
.appContainer {
  background: #ccc;
  padding: 20px;
}
</style>
