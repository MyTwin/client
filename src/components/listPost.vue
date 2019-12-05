<template>
    <div class="list-post">
        <singlePost 
            v-for="post in posts" 
            :key="post.id"
            :result="post"
            >
        </singlePost>
    </div>
</template>

<script>
import singlePost from './post'

export default {
    props: ['posts'],
    components: {
        singlePost
    }
}
</script>

<style scoped>

</style>