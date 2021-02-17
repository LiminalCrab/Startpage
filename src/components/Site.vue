<template>
<li>

    <span> {{ siteName }} <!-- array --> </span>
    <button>Edit</button>
    <button @click="$emit('site-remove')">Remove</button>
</li>
</template>

<script>
export default {

    data: function() {
        return{
            isEditable: false,
            newSiteName: ""
        };
    }, 
    props: {
        siteName: String,
    },
    methods: {
       
    }
}
</script>


<style scoped>

</style>