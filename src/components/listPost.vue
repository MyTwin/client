<template>
    <div class="list-post">
        <singlePost 
            v-for="post in posts" 
            :key="post._id"
            :result="post"
            @do-fetch="fetchData"
            >
        </singlePost>
    </div>
</template>

<script>
import singlePost from './post'

export default {
    props: ['posts'],
    methods: {
        fetchData(){
            this.$emit('fetch-data')
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