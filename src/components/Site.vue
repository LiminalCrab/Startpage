<template>
<li>

    <span> {{ siteName }} <!-- array --> </span>
        <form @submit.prevent="stopEdit()">
            <input
                type="text"
                v-model="newSiteName"
                @blur="stopEdit()"
                ref="fnewSite"
            />
        </form>
    <button @click="doEdit()">Edit</button>
    <button @click="$emit('site-remove')">Remove</button>
</li>
</template>

<script>
export default {

    data: function() {
        return{
            isEditable: false,
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