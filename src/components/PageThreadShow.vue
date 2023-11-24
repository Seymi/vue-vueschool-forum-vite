<template>
    <div class="col-large push-top">
        <h1>{{ thread.title }}</h1>

    <p>
        By <a href="#" class="link-unstyled">{{ getUserById(thread.userId).name }}</a>, 2 hours ago.
        <span style="float:right; margin-top: 2px;" class="hide-mobile text-faded text-small">3 replies by 3 contributors</span>
    </p>

  <div class="post-list">

      <div v-for="postId in thread.posts" :key="postId" class="post">

          <div class="user-info">
              <a href="profile.html#profile-details" class="user-name">{{ getUserById(getPostById(postId).userId).name }}</a>

              <a href="profile.html#profile-details">
                  <img class="avatar-large" :src="getUserById(getPostById(postId).userId).avatar" alt="">
              </a>

              <p class="desktop-only text-small">107 posts</p>

              <p class="desktop-only text-small">23 threads</p>

              <span class="online desktop-only">online</span>

          </div>

          <div class="post-content">
              <div>
                <p>{{ getPostById(postId).text }}</p>
              </div>
              <a href="#" style="margin-left: auto;" class="link-unstyled" title="Make a change"><i class="fa fa-pencil"></i></a>
          </div>



          <div class="post-date text-faded">
              6 hours ago
          </div>

          <div class="reactions">
              <ul>
                  <li>💡</li>
                  <li>❤️</li>
                  <li>👎</li>
                  <li>👍</li>
                  <li>👌</li>
              </ul>
              <button class="btn-xsmall"><span class="emoji">❤️</span>️ 3</button>
              <button class="btn-xsmall active-reaction"><span class="emoji">👌️</span>️ 1</button>
              <button class="btn-xsmall">+ <i class="fa fa-smile-o emoji"></i></button>
          </div>

      </div>

      <div class="post">

          <div class="user-info">
              <a href="profile.html#profile-details" class="user-name">Joseph Kerr</a>

              <a href="profile.html#profile-details">
                  <img class="avatar-large" src="https://i.imgur.com/OqlZN48.jpg" alt="">
              </a>

              <p class="desktop-only text-small">116 posts</p>

              <p class="desktop-only text-small">73 threads</p>

              <span class="online desktop-only">online</span>

          </div>

      </div>

  </div>
</div>
</template>

<script>
import SourceData from '@/data.json';

export default {
    props: {
        id: {type: String, required: true}

    },
    data() {
        return {
            threads: SourceData.threads,
            posts: SourceData.posts,
            users: SourceData.users
        }
    },
    computed: {
        thread() {
            return this.threads.find(thread => thread.id === this.id);
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
