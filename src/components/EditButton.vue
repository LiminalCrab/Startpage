<template>
    <svg xmlns="http://www.w3.org/2000/svg">
    </svg>
</template>

<script>
export default {
    props: {
        iconName: {
            type: String,
            default: 'box'
        },
        width: {
            type: [Number, String],
            default: 18
        },
        height: {
            type: [Number, String],
            default: 18
        },
        iconColor: {
            type: String,
            default: 'currentColor'
        }
    }
    
}
</script>


<style scoped>
svg {
  display: inline-block;
  vertical-align: baseline;
  margin-bottom: -2px;
}
</style>