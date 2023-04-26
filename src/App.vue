<template>
  <div v-if="Mobileres == 1">
    <MainComponentMobile :Mobileres="Mobileres"/>
  </div>
  <div v-else>
    <MainComponentWeb :Mobileres="Mobileres"/>
  </div>
</template>

<script>
import MainComponentWeb from './components/MainComponentWeb.vue'
import MainComponentMobile from './components/MainComponentMobile.vue'

export default {
  name: 'App',
  components: {
    MainComponentWeb,
    MainComponentMobile,
  },
  data(){
    return{
      Mobileres:0,
    }
  },
  methods: {
    winWidth() {
      setInterval(() => {
        var w = window.innerWidth;
        if (w < 768) {
            this.Mobileres = 1
        } else if (w < 960) {
            this.Mobileres = 2
        } else if (w < 1200) {
            this.Mobileres = 3
        } else {
            this.Mobileres = 4
        }
      }, 100);
    }
  },
  mounted() {
    this.winWidth()
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;

}
</style>
