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

<script setup>
    import SourceData from '@/data.json';
    import { ref } from 'vue';

    const threads = ref(SourceData.threads);
    const posts = ref(SourceData.posts);
    const users = ref(SourceData.users);

    function getUserById(userId) {
        return users.value.find(u => u.id === userId);
    }

    function getPostById(postId) {
        return posts.value.find(p => p.id === postId);
    }
</script>

<style scoped>
</style>
