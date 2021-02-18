<template>
<div class="container">
    <li> 
        <span><a :href="staticRef + siteName">{{ siteName }}</a> <!-- array {{ siteName }} --> </span> 
        <button @click="doEdit() ; isHidden = !isHidden"> Toggle-Edit </button>
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
}

</style>