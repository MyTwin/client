<template>
    <div class="box-image">
        <div class="image-wrapper">
            <img :src="srcUser">
        </div>
        <div class="image-wrapper">
            <img :src="srcResult">
        </div>
    </div>
</template>

<script>
export default {
    props: ['srcUser', 'srcResult'],
}
</script>

<style scoped>
    .box-image {
        height: 80vh;
        width: 90vw;
        margin: 0 auto;
        display: flex;
        justify-content: space-evenly;
    }
    .image-wrapper {
        display: flex;
        justify-content: center;
        align-items: center;
        overflow: hidden;
        box-shadow: 0px 8px 10px rgba(0, 0, 0, 0.6);
        cursor: pointer;
    }
    .image-wrapper img {
        width: 400px;
        flex-shrink: 0;
        min-width: 100%;
        min-height: 100%    
    }
</style>