<template>
<span><icon-base class="button"><icon-edit/></icon-base></span>
</template>

<script>
import IconBase from './IconBase.vue'
import IconEdit from './navigation/icons/IconEdit.vue';

export default {
    components: {IconBase, IconEdit},
    props:{


    }
}
</script>

<style scoped>
.button{
    cursor: pointer;
}
</style>