<template>
<div class="c-site-container">
    <li class="c-list"> 
        <span class="c-spanlol"><a class="c-anc" :href="staticRef + siteName">{{ siteName }}</a>
         <!-- array {{ siteName }} --> </span> 
        <button class="c-btn" @click="doEdit() ; isHidden = !isHidden"><nav-edit-btn/></button>
        <button class="c-btn" @click="$emit('site-remove')">Remove</button>
    </li>
    <form class="c-form" @submit.prevent="stopEdit()" v-if="!isHidden">
            <input class="c-input"
                type="text"
                v-model="newSiteName"
                @blur="stopEdit()"
            />
        </form>
</div>
</template>

<script>

import NavEditBtn from './NavEditBtn.vue'

export default {

    components: {
        NavEditBtn
    },

    data: function() {
        
        return{
            isEditable: false,
            isHidden: true,
            newSiteName: ""
        };
    }, 
    props: {
        siteName: String,
        staticRef: String,
    },
    methods: {
        doEdit(){
            if (this.isEditable){
                this.stopEdit();
                console.log("Clicked");
            } else {
                this.newSiteName = this.siteName;
                this.isEditable = true;
                console.log("Clicked");
            }
        },
        stopEdit(){
            this.isEditable = false;
            this.$emit("edit-el", this.newSiteName)
        }
       
    }
};
</script>

<style scoped>

.c-btn{
    color: inherit;
    border: none;
    background: none;
    cursor: pointer;
    margin-left: 10px;
    padding: 0;
}

</style>