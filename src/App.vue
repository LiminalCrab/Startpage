<template>
  <div id="app">
  <!-- Injection goes here -->
    <time-component/>
    <weather/>
    <div class="search"> 
      <form method="get" action="http://www.google.com/search">
      <input type='text' name='q' size="40" maxlength="255" value="" placeholder="Search..."/></form>
    </div>
          <button class="root-btn" @click="addListContainer">+</button>
      <div class="root-td" v-for="item in array" :key="item.id">
          <listcontainer class="root-listcontainer-i" :item="item"/>
      </div>
  </div>
</template>

<script> // Import components here.
import TimeComponent from './components/Time.vue'
import listcontainer from "./components/ListContainer.vue"
import weather from './components/Weather.vue'

//Icons
const AKEY = "list-obj-storage";
let uuid = 1;

export default {
  name: 'App',
  components: {
    TimeComponent,
    listcontainer,
    weather,

    //icons  
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
        console.log("App.vue/Watch: new array data saved", val)
      },
      deep: true
    },
  },
  
  methods:{
    addListContainer(){
      console.log("addList clicked")
      if(this.array.length < 4){
        this.array.push({id: JSON.stringify(++uuid), title: "title1", siteName:["www.test.com"]})
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
    padding: 0px;
    outline:none;
    font-size: 30px;
}

.root-td{
  display: inline-block;
}


</style>
