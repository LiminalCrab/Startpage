<template>
    <div>

    </div>
</template>

<script>

import sites from "./Site.vue"
import createsite from "./CreateSite.vue"
import sitelist from "./SiteList.vue"
import listcreate from "./ListCreate"

export default {
    name: "list-create",
    props: {

    },
    methods: {

    },
    components: { sitelist, createsite, sites, listcreate}  
};

</script>

<style scoped>

</style>