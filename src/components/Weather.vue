<!-- This is weather parent. -->
<template>
<div> 
<span> {{ infodata }} </span>
</div>
</template>

<script>

//okay weird shit to see if Axios is working...
let apiURI = 'http://api.openweathermap.org/data/2.5/weather?q=Atlanta,GA,US&appid=c0700da2a320f44181f321de952c8dc3'

export default {
    name: "weather",
    components: {

    },
    data: function(){
       return { 
           infodata: null,
           loading: true,
           errored: false,
       };
    },
    mounted: function(){
        this.fetchWeatherAPI()
    },

    methods:{
        fetchWeatherAPI(){
        this.$http.get(apiURI)
        .then(response => (this.infodata = response.data.bpi))
        console.log("Weather.vue/methods/fetchWeatherAPI() called.", this.infodata)
        }
    }
}
</script>

