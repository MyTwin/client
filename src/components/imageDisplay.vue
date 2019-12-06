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
        width: 80vw;
        height: calc(100vh - 3rem);
        margin: 0 auto;
        display: flex;
        justify-content: center;
        align-items: center;
    }
    .image-wrapper {
        width: 400px;
        height: 500px;
        display: flex;
        justify-content: center;
        align-items: center;
        overflow: hidden;
        box-shadow: 0px 8px 10px rgba(0, 0, 0, 0.6);
        cursor: pointer;
    }
    .image-wrapper img {
        flex-shrink: 0;
        min-width: 100%;
        min-height: 100%;
    }
</style>