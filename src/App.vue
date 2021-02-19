<template>
  <div id="app">
  <!-- Injection goes here -->
    <time-component/>
    <table>
    <tr>
    <td><listcontainer/></td>
    <td><listcontainer/></td>
    <td><div><button>MAKE NEW LIST</button></div></td>
    </tr>
    </table>
  </div>
</template>

<script> // Import components here.
import TimeComponent from './components/Time.vue'
import listcontainer from "./components/ListContainer.vue"

export default {
  name: 'App',
  components: {
    TimeComponent,
    listcontainer,
  },
  methods:{
    addListContainer(){
    
    }

  }
  
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
