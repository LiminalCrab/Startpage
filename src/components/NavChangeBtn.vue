<template>
<span><icon-base class="button" height="18" width="10"><icon-change/></icon-base></span>
</template>

<script>
import IconBase from './IconBase.vue'
import IconChange from './navigation/icons/IconChange.vue';

export default {
    components: {IconBase, IconChange},
}
</script>

<style scoped>
.button{
    cursor: pointer;
}
</style>