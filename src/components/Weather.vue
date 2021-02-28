<!-- This is weather parent. -->
<template>
<div> 
<span> {{ apidata }} </span>
</div>
</template>

<script>
let apiURI = 'http://api.openweathermap.org/data/2.5/weather?q=Atlanta,GA,US&appid=c0700da2a320f44181f321de952c8dc3'

export default {
    name: "weather",
    components: {

    },
    data: function(){
       return { 
           apidata: {
               city: 'None',
               country: 'None',
               temperature: 'None'

           },
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
            .then(function(response){ 
                console.log(response)});

            console.log("Weather.vue/methods/fetchWeatherAPI() called.")
        }
    }
}
</script>

