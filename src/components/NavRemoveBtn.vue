<template>
<span><icon-base class="button"><icon-remove/></icon-base></span>
</template>

<script>
import IconBase from './IconBase.vue'
import IconRemove from './navigation/icons/IconRemove.vue';

export default {
    components: {IconBase, IconRemove},
}
</script>

<style scoped>
.button{
    cursor: pointer;
}
</style>