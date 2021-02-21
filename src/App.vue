<template>
  <div id="app">
  <!-- Injection goes here -->
    <time-component/>
    <table>
      <tr>
        <button @click="addListContainer">New List </button>
        <td v-for="item in array" :key="item.id">
          <listcontainer class="listcontainerDecor" :item="item"/>
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
  font-family:monospace;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  margin-top: 60px;
  background-color: #fff;
}

.listcontainerDecor:hover{
  background-color: black;
  color: #fff;

}
</style>
