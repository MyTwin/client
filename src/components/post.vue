<template>
    <div class="post-wrapper">
        <div class="avatar">
            <img :src="result.UserId.avatar" alt="">
            <h4>{{result.UserId.username}}</h4>
        </div>

        <div class="image-wrapper">
            <div class="post-img">
                <img :src="result.image">
            </div>
            <div class="post-img">
                <img :src="result.resultImage">
                <label class="celeb-name">Emma Watson</label>
            </div>
        </div>

        <div class="action-wrapper">
            <div><a :href="`https://www.facebook.com/sharer/sharer.php?u=${result.resultImage}&quote=${result.caption}`" target="_blank"><span><i class="fab fa-facebook" style="margin-right: 5px;"></i></span></a></div>
            <div class="like" :class="liked" @click="likeThis(result._id)"></div>
            <div class="like-count">{{ result.likes.length }}</div>
        </div>
        <label>
            {{ result.caption }}
        </label>
    </div>
</template>

<script>

import axios from 'axios'

export default {
    props: ['result'],
    data() {
        return {
            liked: '',
            baseUrl: 'http://localhost:3000'
        }
    },
    methods: {
        likeThis(id) {
            axios({
                url: `${this.baseUrl}/post/${id}/likes`,
                method: 'PUT',
                headers:{
                    access_token: localStorage.getItem('token')
                }
            })
            .then(({data})=>{
                if(data.message == 'Give Like Success'){
                    this.liked = 'liked'
                }else{
                    this.liked = ''
                }
                this.$emit('do-fetch')
            })
            .catch(err => {
                console.log(err)
            })
        }
    },
    computed:{
        shareFacebook(){
        return `https://www.facebook.com/sharer/sharer.php?u=${this.linkImage}&quote=${this.desc}`
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