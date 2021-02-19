<template>
    <div>

    </div>
</template>

<script>

import sites from "./Site.vue"
import createsite from "./CreateSite.vue"
import sitelist from "./SiteList.vue"

export default {
    name: "list-create",
    props: {

    },
    methods: {

    },
    components: { sitelist, createsite, sites}  
};

</script>

<style scoped>

</style>