<template>
<div class="container">
    <li> 
        <span> {{ siteName }} <!-- array --> </span> 
        <button @click="doEdit() ; isHidden = !isHidden"> Edit </button>
        <button @click="$emit('site-remove')">Remove</button>
    </li>
    <form @submit.prevent="stopEdit()" v-if="!isHidden">
            <input
                type="text"
                v-model="newSiteName"
                @blur="stopEdit()"
                ref="fnewSite"
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
    },
    methods: {
        doEdit(){
            if (this.isEditable){
                this.stopEdit();
            } else {
                this.newSiteName = this.siteName;
                this.isEditable = true;
                this.$nextTick(() => this.$refs.fnewSite.focus());
            }
        },
        stopEdit(){
            this.isEditable = false;
            this.$emit("site-edit", this.newSiteName)
        }
       
    }
};
</script>


<style scoped>

</style>