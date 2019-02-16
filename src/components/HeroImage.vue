<template>
    <div class="heroImage"></div>
</template>

<script>
export default {
    name: 'HeroImage',
}
</script>

<style lang="scss" scoped>

.heroImage {
    position: fixed;
    top: 0;
    width: 100%;
    height: 100vh;
    background-image: url('../assets/header.jpg');
    background-size: cover;
    background-position: 60% 0%;   
    background-repeat: no-repeat;
    z-index: -1;
}
   
</style>
