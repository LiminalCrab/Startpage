<template>
<div class="container">
    <li class="listDec"> 
        <span><a class="linkDec" :href="staticRef + siteName">{{ siteName }}</a> <!-- array {{ siteName }} --> </span> 
        <button class="togglebutton" @click="doEdit() ; isHidden = !isHidden"> Toggle-Edit </button>
        <button @click="$emit('site-remove')">Remove</button>
    </li>
    <form @submit.prevent="stopEdit()" v-if="!isHidden">
            <input
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
.container{
    border: 1px solid;
    color: #fff;
    }
.container:hover a{
    background-color: #000;
    color: white;
}

.linkDec{
    text-decoration: none;
    color: #000;
}

.listDec{
    list-style-type: none;
}


</style>