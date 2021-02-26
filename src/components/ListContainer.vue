<template>
    <div class="parent-listcontainer">
        <sitelist @changeLabel="setSiteLabel" :siteListLabel="siteListLabel_d"/>
    </div>
</template>

<script>

import sitelist from "./SiteList.vue"
import '@/assets/list.css'

const LKey = "list-label-data"

export default {
    props: {
        item: {
            type: Object,
            required: true
        },
    },
    data(){
        return {
            siteListLabel_d: "Title",

        };
    },
    methods: {
        setSiteLabel(siteListLabel){
            this.siteListLabel_d = siteListLabel;
            localStorage.setItem(LKey, JSON.stringify(this.siteListLabel_d));
        },
    },
    components: { sitelist }  
};

</script>


