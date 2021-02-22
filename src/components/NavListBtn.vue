<template>
<span><icon-base class="button"><icon-list/></icon-base></span>
</template>

<script>
import IconBase from './IconBase.vue'
import IconList from './navigation/icons/IconList.vue';

export default {
    components: {IconBase, IconList},
    props:{


    }
}
</script>

<style scoped>
.button{
    cursor: pointer;
}
</style>