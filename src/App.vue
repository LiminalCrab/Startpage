<template>
  <div id="app">
  <!-- Injection goes here -->
    <time-component/>
    <table class="root-tbl">
      <tr class="root-tbl-tr">
        <button class="root-btn" @click="addListContainer"><nav-list-btn/></button>
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

//Icons
import NavListBtn from './components/NavListBtn.vue'

const AKEY = "list-obj-storage";
let uuid = 1;

export default {
  name: 'App',
  components: {
    TimeComponent,
    listcontainer,

    //icons
    NavListBtn
  
  },
  beforeCreate(){
    this.uuid = uuid.toString();
    this.item = JSON.parse(localStorage.getItem(AKEY))
  },

  data(){
    return { 
      array: [{id: 1}] 
      };
  },
  created(){
  },

  methods:{
    addListContainer(){
      if(this.array.length < 3){
    this.array.push({id: ++uuid})
    localStorage.setItem(AKEY, JSON.stringify(this.array))
      } else {
        console.log("You can't create more of these components...")
      }
    },
  },

};
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

.root-btn{
  cursor: pointer;
    border: none;
    background: none;
    cursor: pointer;
    margin-left: 310px;
    margin-top: 190px;
    padding: 0;
    outline:none;
}

</style>
