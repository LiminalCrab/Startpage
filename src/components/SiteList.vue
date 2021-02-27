<template>
   <div class="child-sitelist-container">

        <span class="c-label-span">{{ siteListLabel }}</span>

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
           v-for="(site, index) in item.siteName" 
           :key="index"
           :siteName="site"
           @site-remove="removeSite(site)"
           @edit-el="editSite(index, $event)"
           />
           <!-- addSite method from CrateSite.vue -->
        <create-site class="c-createsite" @on-new-site="addSite($event)" />
      </ul>
    </div>
</template>

<script>

import Site from "./Site.vue"
import createSite from "./CreateSite.vue"
import '@/assets/list.css'
import Vue from 'vue'

//icon
import NavChangeBtn from './NavChangeBtn.vue';
// const SKEY = "site-list-data";
let uuid = 1;

export default {
    name: "siteList",
    props: {
        siteListLabel: String,
        item: {
            type: Object,
            required: true
        },
    },
    data(){
        return {
            sites: [ {aIdent: "1", staticRef: "https://", siteName: "www.cnn.com" }, 
                     {aIdent: "2", staticRef: "https://", siteName: "www.nyt.com" }, 
                     {aIdent: "3", staticRef: "https://", siteName: "washingtonpost.com" }
            ],
            // Shouldn't edit props so I made this which is based off
            // the value of the prop but not using the prop directly.
            siteListLabel_d: ""

        };
    },
    beforeCreate(){
    this.uuid = uuid.toString();
    },

    created(){
       // this.sites = JSON.parse(localStorage.getItem(SKEY) || "[]")
        // console.log("Getting storage from SiteList.vue in Site")
    },
    computed:{

    },
    methods: {
        addSite(newSite){
            if(this.sites.length < 15){
            this.item.siteName.push(newSite);
           // localStorage.setItem(SKEY, JSON.stringify(this.sites));
            } else {
                console.log("You can't add anymore.")
            }
                    },
        // create a new array (callback)
        removeSite(removedSite){
            this.item.siteName = this.item.siteName.filter(site => site !== removedSite);
        },
        editSite(index, newSiteName){
            Vue.set(this.item.siteName, index, newSiteName)
            console.log(index, newSiteName)
        },
        changeLabel(){
            if (this.siteListLabel_d.length > 0){
            this.$emit("changeLabel", this.siteListLabel_d);
            this.siteListLabel_d = "";
            }
        }
    },
    components: { Site, createSite, NavChangeBtn }
};

</script>
