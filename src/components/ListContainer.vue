<template>
    <div class="parent-listcontainer">
        <sitelist @changeLabel="setSiteLabel" :siteListLabel="item.title" :item="item"/>
    </div>
</template>

<script>

import sitelist from "./SiteList.vue"
import '@/assets/list.css'

export default {
    props: {
        item: {
            type: Object,
            required: true
        },
    },
    data(){
        return {
            siteListLabel_d: "Test"
        };
    },
    methods: {
        setSiteLabel(siteListLabel){
            this.item.title = siteListLabel;
            this.siteListLabel_d = siteListLabel;
        },
    },
    components: { sitelist }  
};

</script>


