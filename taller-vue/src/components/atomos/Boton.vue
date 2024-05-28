<script>
export default{
    props: [
        'texto',
        'css'
    ]
};
</script>
<template>
    <button class="btn" :class="css">{{ texto }}</button>
</template>
<style scoped>

</style>