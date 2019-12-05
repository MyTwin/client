<template>
    <div class="post-wrapper">
        <div class="post-img" @click="doThis">
            <img :src="result.userImage">
        </div>
        <div class="post-img">
            <img :src="result.resultImage">
        </div>
        <div class="action-wrapper">
            <button>LIKE</button>
            <button>SHARE</button>
        </div>
    </div>
</template>

<script>
export default {
    props: ['result'],
    methods: {
        doThis(event) {
            this.$emit('dodo', 'aku kirim nih')
        }
    }
}
</script>

<style>
    .post-wrapper {
        position: relative;
        width: 200px;
        height: 200px;
        display: flex;
        margin: 1rem;
    }
    .post-wrapper:hover>.action-wrapper {
        background-color: rgba(0, 0, 0, 0.5);
        transition: 0.4s background-color;
    }
    .action-wrapper:hover>button {
        display: block;
    }
    .post-wrapper button {
        display: none;
        cursor: pointer;
    }
    .action-wrapper {
        position: absolute;
        top:0;
        left: 0;
        width: 100%;
        height: 100%;
        background-color: rgba(0, 0, 0, 0);
        display: flex;
        justify-content: center;
        align-items: center;
    }
    .post-img {
        display: flex;
        justify-content: center;
        align-items: center;
        overflow: hidden;
    }
    .post-img img {
        width:200px;
        flex-shrink: 0;
        min-width: 100%;
        min-height: 100%    
    }
</style>