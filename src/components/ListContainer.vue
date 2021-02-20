<template>
    <div class="large-container">
        <sitelist @changeLabel="setSiteLabel" :siteListLabel="siteListLabel_d"/>
    </div>
</template>

<script>

import sitelist from "./SiteList.vue"

export default {
    name: "list-container",
    props: {
        item: {
            type: Object,
            required: true
        }
    },
    data(){
        return {
            siteListLabel_d: "",

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
.large-container{
    padding: 20px;
    margin-left: 20px;
    margin-top: 200px;
    border: 1px solid;
    max-width: 400px;
}
</style>