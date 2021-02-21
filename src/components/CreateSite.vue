<template>
    <form class="c-form" @submit.prevent="addSite()">
    <input class="c-input"
    v-model="newSite"
    type="text"
    placeholder="Add a new site..."
     />
     </form>
</template>

<script>
import '@/assets/list.css'

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