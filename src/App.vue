<template>
  <div id="app">
  <!-- Injection goes here -->
    <time-component/>
    <table class="root-tbl">
      <tr class="root-tbl-tr">
        <button class="root-btn" @click="addListContainer">New List </button>
        <td class="root-td" v-for="item in array" :key="item.id">
          <listcontainer class="root-listcontainer-i" :item="item"/>
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
  font-family: monospace;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  margin-top: 60px;
  background-color: #fff;
}
</style>
