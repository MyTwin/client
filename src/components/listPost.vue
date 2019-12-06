<template>
    <div class="list-post">
        <singlePost 
            v-for="post in posts" 
            :key="post.id"
            :result="post"
            @test="doThis"
            >
        </singlePost>
    </div>
</template>

<script>
import singlePost from './post'

export default {
    props: ['posts'],
    methods: {
        doThis(v) {
            console.log(v)
        }
    },
    components: {
        singlePost
    }
}
</script>

<style scoped>
    .list-post {
        display: flex;
        flex-direction: column;
        align-items: center;
        width: 80vw;
        margin: auto;
        padding-top: 2rem;
    }
</style>