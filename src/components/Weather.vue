<template>
<div class="weather">
    <div class="location-container">
        <div class="p-location"> {{ wdata.name }}, {{ wdata.sys.country }} </div>
        
        <div class="p-temp"> {{ Math.round(wdata.main.temp) }} °F </div>
    </div>
</div>
</template>

<script>

import '@/assets/list.css'


export default {
    name: "weather",
    components: {

    },
    data: function(){
       return { 
           api_key: 'c0700da2a320f44181f321de952c8dc3',
           api_URI: 'http://api.openweathermap.org/data/2.5/',
           wdata: { },
           getLocation: null,
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
                    fetch(`${this.api_URI}weather?lat=${this.lat}&lon=${this.long}&units=imperial&appid=${this.api_key}`)
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
        setData(results){
            this.wdata = results;
            console.log(this.wdata.main.temp)
        }
    }
}
</script>

