<template>
  <div class="post-wrapper">
        <div class="post-img">
            <img :src="result.userImage">
        </div>
        <div class="post-img">
            <img :src="result.resultImage">
        </div>
    </div>
</template>

<script>
export default {
    props: ['result']
}
</script>

<style>
    .post-wrapper {
        width: 200px;
        height: 300px;
        margin: 0 auto;
        display: flex;
    }
    .post-image {
        width: 200px;
        display: flex;
        justify-content: center;
        align-items: center;
        overflow: hidden;
    }
    .post-img {
        flex-shrink: 0;
        min-width: 100%;
        min-height: 100%    
    }
</style>