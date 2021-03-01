<template>
    <div class="date-time">
        <h1> {{ date }} </h1>
    </div>
</template>

<script>
import moment from 'moment'
import '@/assets/list.css'


export default {
    name: "get-time",
    data: function() { return {
        date: moment().format('h:mm a')
        }
    },
    mounted: function(){
        setInterval(() => {
            this.date = moment().format('h:mm a');
        }, 50000);
    }
}

</script>

<style scoped>

h1{
    color: #000;
}

</style>