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
  },
  created(){
    if(localStorage.getItem(AKEY)){
      this.array = JSON.parse(localStorage.getItem(AKEY))
      console.log("Default AKEY existed.")
    } else {
      //this.item = localStorage.setItem(AKEY,'[id:"1"]');
      this.array = [{id: "1", title: "title1", siteName:["www.test.com"]}]
      console.log("Created.") }
  },
  data(){
    return { 
      array: [{id: "1", title: "title1", siteName:["www.test.com"]}],
      }
    },
  watch: {
    array: { 
      handler: function(val) { 
        localStorage.setItem(AKEY, JSON.stringify(val))
        console.log("App.vue/Watch: listContainer saved.", val)
      },
      deep: true
    },
  },
  
  methods:{
    addListContainer(){
      console.log("addList clicked")
      if(this.array.length < 5){
        this.array.push({id: JSON.stringify(++uuid)})
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
