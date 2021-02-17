<template>
    <form @submit.prevent="addSite()">
    <input
    v-model="newSite"
    type="text"
    placeholder="Add a new site..."
     />
     </form>
</template>

<script>
export default {
    data: function(){ 
        return{
            newSite: ""
        }; 
    },
    methods: {
        addSite(){
            if (this.newSite.length > 0){
                this.$emit("on-new-site", this.newSite);
            }
        }

    }
}


</script>

<style scoped>

</style>