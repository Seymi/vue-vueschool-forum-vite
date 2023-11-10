<template>
    <div>
        <h1>Hallo from PageHome</h1>
        <div v-for="thread in threads" :key="thread.id">
            <h2>{{ thread.title }}</h2>
            <div v-for="postId in thread.posts" :key="postId">
                <p>{{ getUserById(getPostById(postId).userId).name }}</p>
                <p>{{ getPostById(postId).text }}</p>
            </div>

        </div>
    </div>
</template>

<script>
import SourceData from '@/data.json';

export default {
    data() {
        return {
            threads: SourceData.threads,
            posts: SourceData.posts,
            users: SourceData.users
        }
    },
    methods: {
        getUserById(userId) {
            return this.users.find(u => u.id === userId);
        },
        getPostById(postId) {
            return this.posts.find(p => p.id === postId);
        }

    }
}

</script>

<style scoped>
</style>
