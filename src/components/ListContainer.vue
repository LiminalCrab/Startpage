<template>
    <div class="large-container">
        
        <sitelist @changeLabel="setSiteLabel" :siteListLabel="siteListLabel_d"/>
    </div>
</template>

<script>

import sitelist from "./SiteList.vue"

export default {
    name: "list-create",
    data(){
        return {
            siteListLabel_d: "Test"
        };
    },
    methods: {
        setSiteLabel(siteListLabel){
            this.siteListLabel_d = siteListLabel;
        },
    },
    components: { sitelist }  
};

</script>

<style scoped>

</style>