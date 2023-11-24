<template>
    <div class="col-full">
        <div class="thread-list">
            <h2 class="list-title">Threads</h2>

            <div v-for="thread in threads" :key="thread.id" class="thread">
                <div>
                    <p>
                        <a href="thread.html">{{ thread.title }}</a>
                    </p>
                    <p class="text-faded text-xsmall">
                        By <a href="profile.html">{{ getUserById(thread.userId).name }}</a>, {{ thread.publishedAt }} yesterday.
                    </p>
                </div>

                <div class="activity">
                    <p class="replies-count">{{ numberRepliesText(thread.posts.length) }}</p>
                    <img class="avatar-medium" :src="getUserById(thread.userId).avatar" alt="Avatar">

                    <div>
                        <p class="text-xsmall">
                            <a href="profile.html">{{ getUserById(thread.userId).name }}</a>
                        </p>
                        <p class="text-xsmall text-faded">{{ thread.publishedAt }} 2 hours ago</p>
                    </div>
                </div>
            </div>

        </div>

    </div>

</template>

<script setup>
    import SourceData from '@/data.json';
    import { reactive } from 'vue';

    //const posts = reactive(SourceData.posts);
    const users = reactive(SourceData.users);

    // const props =  ... then we use  ...  props.threads
    defineProps({
        threads: {
                type: Array,
                required: true
        }
    })

    function getUserById(userId) {
        return users.find(u => u.id === userId);
    }


    /*
    function getPostById(postId) {
        return posts.find(p => p.id === postId);
    }
    */

    function numberRepliesText(cnt) {
        if (cnt === 1) {return '1 Antwort'}
        else { return `${cnt} Antworten`}
    }

    /*
    getLastReply(cnt) {

    }
    */
</script>



<style>

</style>
