<template>
    <div class="list-post">
        <singlePost 
            v-for="post in posts" 
            :key="post.id"
            :result="post"
            @dodo="doThis"
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
        flex-wrap: wrap;
        justify-content:center;
        width: 80vw;
        margin: auto;
    }
</style>