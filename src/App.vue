<template>
  <div id="app">
  <!-- Injection goes here -->
    <time-component/>
    <button @click="addListContainer">New List </button>
    <table>
      <tr v-for="item in array" :key="item.id">
        <td>
          <listcontainer :item="item"/>
         </td>
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
  data(){
    return { array: [] };
  },
  methods:{
    addListContainer(){
    this.array.push({id: Math.random() })
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
