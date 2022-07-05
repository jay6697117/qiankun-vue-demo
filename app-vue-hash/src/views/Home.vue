<template>
  <div class="home">
    <img alt="Vue logo" src="../assets/logo.png" />
    <span style="color:red;" v-if="isQiankun" @click="changeParentState">主项目的数据：{{ commonData.parent }},点击变为666</span>
    <HelloWorld msg="Welcome to Your Vue.js App" />
  </div>
</template>

<script>
// @ is an alias to /src
import HelloWorld from '@/components/HelloWorld.vue';

export default {
  name: 'Home',
  components: {
    HelloWorld
  },
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
    console.log('app-vue-hash Home.vue mounted');
    console.log('Home.vue mounted window:', window);
  },
  methods: {
    changeParentState() {
      if (this.isQiankun) {
        this.$root.parentVuex.commit('setCommonData', { parent: 666 });
      }
    }
  }
};
</script>
