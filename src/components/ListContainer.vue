<template>
    <div class="parent-listcontainer">
        <sitelist @changeLabel="setSiteLabel" :siteListLabel="siteListLabel_d"/>
    </div>
</template>

<script>

import sitelist from "./SiteList.vue"
import '@/assets/list.css'

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
            siteListLabel_d: "Title",

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
.parent-listcontainer{
    padding: 20px;
    margin-left: 20px;
    margin-top: 200px;
    border: 1px solid;
    max-width: 400px;
    background-color: rgb(255, 255, 255);
}

.parent-listcontainer:hover{
    background-color: #000;
    color: #fff;
}


</style>



