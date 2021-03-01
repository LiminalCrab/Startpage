<!-- This is weather parent. -->
<template>
<div class="weather">
    <div class="location-container">
        <div class="p-location" v-if="city !== ''">{{ this.city }}, {{ wdata.sys.country }} </div>
 
    </div>
</div>
</template>

<script>

export default {
    name: "weather",
    components: {

    },
    data: function(){
       return { 
           api_key: 'c0700da2a320f44181f321de952c8dc3',
           api_URI: 'http://api.openweathermap.org/data/2.5/',
           wdata: { },
           city: '',
           state: '',
           getLocation: null,
           fetchData: '',
           long: '',
           lat: '',
       }
    },
    mounted: function() {

        for (var i = 0; i < 2; i++){
            if (navigator.geolocation){
                navigator.geolocation.getCurrentPosition(pos => {
                    this.getLocation = true;
                    this.long = pos.coords.longitude;
                    this.lat = pos.coords.latitude;
                    console.log(this.long, this.lat)
                    fetch(`${this.api_URI}weather?lat=${this.lat}&lon=${this.long}&appid=${this.api_key}`)
                        .then (res => {
                            return res.json();
                        }).then(res => { 
                            this.setData(res);
                        });
                }), (error) => {
                    if (error.code == error.PERMISSION_DENIED){
                        this.getLocation = false;
                    }
                }
            }}
    },

    methods: {
        getWeatherData(e){
            for (var i = 0; i < 2; i++){
                if (e.key == "Enter" ){
                    if (this.fetchData.split(",").length == 2){
                        this.city = this.fetchData.split(",")[0].trim();
                        this.city = this.fetchData.split(",")[1].trim();
                        console.log(this.fetchData);
                    }
                    fetch(`${this.api_URI}weather?q=${this.state},${this.city}&appid=${this.api_key}`)
                        .then(res => {
                            return res.json();
                          }).then(this.setData);
                }
            }
        },
    }
}
</script>

