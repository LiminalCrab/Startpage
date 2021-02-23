<template>
   <div class="child-sitelist-container">

        <span class="c-label-span">{{  siteListLabel }}</span>

       <form class="c-form" @submit.prevent="changeLabel()">
           <input class="c-input"
           type="text"
           v-model="siteListLabel_d"
           placeholder="Change title..."
           />
           <button class="c-btn-change" @click="changeLabel"> <nav-change-btn/> </button>
        </form>

       <ul class="c-ul">
           <site
           v-for="(site, index) in sites" 
           :key="index"
           :siteName="site.siteName"
           :staticRef="site.staticRef"
           @site-remove="removeSite(site)"
           @edit-el="editSite(site, $event)"
           />
        <create-site class="c-createsite" @on-new-site="addSite($event)" />
      </ul>
    </div>
</template>

<script>

import Site from "./Site.vue"
import createSite from "./CreateSite.vue"
import '@/assets/list.css'

//icon
import NavChangeBtn from './NavChangeBtn.vue'

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
            if(this.sites.length < 5){
            this.sites.push({ staticRef: "https://", siteName: newSite });
            } else {
                console.log("You can't add anymore.")
            }
        },
        // create a new array (callback)
        removeSite(removedSite){
            this.sites = this.sites.filter(site => site !== removedSite);
        },
        editSite(site, newSiteName){
            site.siteName = newSiteName;
        },
        changeLabel(){
            if (this.siteListLabel_d.length > 0){
            this.$emit("changeLabel", this.siteListLabel_d);
            this.siteListLabel_d = "";
            }
            //this.siteListLabel = this.siteListLabel_d
        }
    },
    components: { Site, createSite, NavChangeBtn }
};

</script>
