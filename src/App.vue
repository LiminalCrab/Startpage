<template>
  <div id="app">
  <!-- Injection goes here -->
    <time-component/>
    <sites-list @changeLabel="setSiteLabel" :siteListLabel="siteListLabel_d"/>
  </div>
</template>

<script> // Import components here.
import TimeComponent from './components/Time.vue'
import SitesList from './components/SiteList.vue'

export default {
  name: 'App',
  data(){
      return {
        siteListLabel_d: "Test"
      };
  },
  methods: { 
    setSiteLabel(siteListLabel){
      this.siteListLabel_d = siteListLabel;
    },

  },
  components: {
    TimeComponent,
    SitesList
  },
}
</script>

<!-- CSS for global -->
<style>
#app {
  font-family:serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  margin-top: 60px;
  background-color: #fff;
}
</style>
