<template>
   <div class="sitelist-container">
        {{  siteListLabel }}
       <form @submit.prevent="changeLabel()">
           <input
           type="text"
           v-model="siteListLabel_d"
           />
           <button @click="changeLabel"> Change </button>
        </form>
       <ul>
           <create-site @on-new-site="addSite($event)" />
           
           <site
           v-for="(site, index) in sites" 
           :key="index"
           :siteName="site.siteName"
           :staticRef="site.staticRef"
           @site-remove="removeSite(site)"
           @edit-el="editSite(site, $event)"
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
        siteListLabel: String,

    },
    data(){
        return {
            sites: [ { staticRef: "https://", siteName: "www.cnn.com" }, 
                     { staticRef: "https://", siteName: "www.nyt.com" }, 
                     { staticRef: "https://", siteName: "washingtonpost.com" }
            ],
            // Shouldn't edit props so I made this which is based off
            // the value of the prop but not using the prop directly.
            siteListLabel_d: ""
        };
    },
    methods: {
        addSite(newSite){
            this.sites.push({ staticRef: "https://", siteName: newSite });
        },
        // create a new array (callback)
        removeSite(removedSite){
            this.sites = this.sites.filter(site => site !== removedSite);
        },
        editSite(site, newSiteName){
            site.siteName = newSiteName;
        },
        changeLabel(){
            this.$emit("changeLabel", this.siteListLabel_d);
            //this.siteListLabel = this.siteListLabel_d
        }
    },
    components: { Site, createSite }
};

</script>

<style scoped>
.sitelist-container:hover{
    color: #fff;
}
</style>