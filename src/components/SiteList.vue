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
        </ul>
    <div class="grid-create-site">
        <create-site class="c-createsite" @on-new-site="addSite($event)" />
    </div>
    </div>
</template>

<script>

import Site from "./Site.vue"
import createSite from "./CreateSite.vue"
import '@/assets/list.css'
import Vue from 'vue'

//icon
import NavChangeBtn from './NavChangeBtn.vue';

export default {
    name: "siteList",
    props: {
        siteListLabel: String,
        item: {
            type: Object,
            required: true
        },
    },
    data: function(){
        return {
            // Shouldn't edit props so I made this which is based off
            // the value of the prop but not using the prop directly.
            siteListLabel_d: ""

        };
    },
    methods: {
        addSite(newSite){
            if(this.item.siteName.length < 4){
                this.item.siteName.push(newSite);
                console.log("Sitelist.vue/methods/addSite:", newSite);
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
                console.log("Sitelist.vue/methods/changeLabel:", this.siteListLabel_d);
                this.siteListLabel_d = "";
            }
        }
    },
    components: { Site, createSite, NavChangeBtn }
};

</script>
