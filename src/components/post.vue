<template>
    <div class="post-wrapper">
        <div class="avatar">
            <img :src="result.userAvatar" alt="">
            <h4>username</h4>
        </div>

        <div class="image-wrapper">
            <div class="post-img">
                <img :src="result.userImage">
            </div>
            <div class="post-img">
                <img :src="result.resultImage">
            </div>
        </div>

        <div class="action-wrapper" @click="doThis">
            <div class="like-count">99</div>
            <div class="like" :class="liked" @click="likeThis"></div>
            <button>SHARE</button>
        </div>
        <label>
            Lorem ipsum dolor sit amet consectetur adipisicing elit. Rem perferendis repellat hic. Quam laudantium molestias illo tempore officia, provident impedit velit dicta id, porro perferendis aut. Illum dicta at nemo?
        </label>
    </div>
</template>

<script>
export default {
    props: ['result'],
    data() {
        return {
            liked: false
        }
    },
    methods: {
        doThis() {
            this.$emit('test', 'aku kirim nih')
        },
        likeThis() {
            if (this.liked === 'liked') {
                this.liked = false
            } else {
                this.liked = 'liked'
            }
        }
    }
}
</script>

<style>
    .post-wrapper {
        position: relative;
        width: 400px;
        margin-bottom: 2rem;
        background-color: #f4efd3;
        padding: 1rem 2rem 2rem;
        box-shadow: 0 10px 8px rgba(0, 0, 0, 0.5);
        border-radius: 8px;
    }
    .avatar {
        display: flex;
        align-items: center;
        padding: 0.4rem 0;
    }
    .avatar img {
        width: 40px;
        border-radius: 50%;
        margin-right: 1rem;
    }
    .image-wrapper {
        display: flex;
        height: 240px;
        height: 240px;

    }
    .post-img {
        display: flex;
        justify-content: center;
        align-items: center;
        overflow: hidden;
    }
    .post-img img {
        width:400px;
        flex-shrink: 0;
        min-width: 100%;
        min-height: 100%    
    }

    .action-wrapper {
        background-color: rgba(0, 0, 0, 0);
        display: flex;
        justify-content: flex-start;
        align-items: center;
    }
    .action-wrapper button {
        cursor: pointer;
    }
    .like {
        cursor: pointer;
        height: 50px;
        width: 50px;
        background-image:url( 'https://abs.twimg.com/a/1446542199/img/t1/web_heart_animation.png');
        background-position: left;
        background-repeat:no-repeat;
        background-size:2900%;
    }

    .liked {
        animation: heart-burst .8s steps(28) 1 forwards;
    }

    @keyframes heart-burst {
        from {background-position:left;}
        to { background-position:right;}
    }
</style>