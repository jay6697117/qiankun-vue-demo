<template>
  <div class="home">
    <HelloWorld msg="Welcome to Your Vue.js App main" />
  </div>
</template>

<script>
// @ is an alias to /src
// import HelloWorld from '@/components/HelloWorld.vue'

export default {
  name: 'Home',
  components: {
    HelloWorld: async () => {
      console.log('main window.commonComponents 0:', window.commonComponents);
      if (window.commonComponents.HelloWorld) return window.commonComponents.HelloWorld;
      const app = window.loadMicroApp({
        name: 'app-vue-history',
        entry: 'http://localhost:2222',
        container: '#hideContainer',
        props: { data: { commonComponents: window.commonComponents } }
      });
      await app.mountPromise;
      console.log('main window.commonComponents 1:', window.commonComponents);
      console.log('main app:', app);
      // app.unmount(); 不能卸载，卸载时会去掉样式的
      return window.commonComponents.HelloWorld;
    }
  },
  data() {
    return {
      // isQiankun: window.__POWERED_BY_QIANKUN__,
    };
  },
  computed: {
    // commonData(){
    //   return this.isQiankun ? this.$root.parentVuex.state.commonData : '';
    // }
  },
  methods: {
    // changeParentState(){
    //   if(this.isQiankun){
    //     this.$root.parentVuex.commit('setCommonData', { parent: 2 });
    //   }
    // }
  }
};
</script>
