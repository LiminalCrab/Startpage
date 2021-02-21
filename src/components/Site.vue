<template>
<div class="c-site-container">
    <li class="c-list"> 
        <span class="c-spanlol"><a class="c-anc" :href="staticRef + siteName">{{ siteName }}</a> <!-- array {{ siteName }} --> </span> 
        <button class="c-btn" @click="doEdit() ; isHidden = !isHidden"> Toggle-Edit </button>
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
export default {

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
            } else {
                this.newSiteName = this.siteName;
                this.isEditable = true;
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
</style>