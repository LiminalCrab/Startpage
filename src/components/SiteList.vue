<template>
   <div class="container">
       {{ siteListName }}

       <ul>
           <create-site @on-new-site="addSite($event)" />

           <site
           v-for="(site, index) in sites" 
           :key="index"
           :siteName="site.siteName"
           @site-remove="removeSite(site)"
           />
      </ul>
    </div>
</template>

<script>

import Site from "./Site.vue"
import createSite from "./CreateSite.vue"

export default {
    name: "site-list",
    props: {
        siteListName: String,
    },
    data(){
        return {
            sites: [ { siteName: "www.cnn.com" }, 
                     { siteName: "www.nyt.com" }, 
                     { siteName: "washingtonpost.com" }
            ],
        };
    },
    methods: {
        addSite(newSite){
            this.sites.push({ siteName: newSite });
        },
        // create a new array (callback)
        removeSite(removedSite){
            this.sites = this.sites.filter(site => site !== removedSite)
        },
    },
    components: { Site, createSite }
};

</script>

<style scoped>

</style>