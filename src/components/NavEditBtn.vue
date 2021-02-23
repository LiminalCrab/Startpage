<template>
<span><icon-base class="button" :height="10" :width="10"><icon-edit/></icon-base></span>
</template>

<script>
import IconBase from './IconBase.vue'
import IconEdit from './navigation/icons/IconEdit.vue';

export default {
    components: {IconBase, IconEdit},
}
</script>

<style scoped>
.button{
    cursor: pointer;
}
</style>