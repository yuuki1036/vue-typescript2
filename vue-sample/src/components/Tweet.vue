<script setup lang="ts">
import { ref } from 'vue';
import TweetPostForm from './TweetPostForm.vue';
import TweetList from './TweetList.vue';

const tweets = ref([
  {
    id: 0,
    desc: "hello world"
  },
  {
    id: 1,
    desc: "yeeaaa"
  },
])

const postTweet = (desc: string) => {
  const tweet = {id: Math.random(), desc}
  tweets.value.push(tweet)
}

const deleteTweet = (id: number) => {
  tweets.value = tweets.value.filter((t) => t.id !== id)
}

</script>

<template>
  <div class="container">
    <h1>tweeter</h1>
    <TweetPostForm @post-tweet="postTweet"/>
    <TweetList :tweets="tweets" @delete-tweet="deleteTweet"/>
  </div>
</template>

<style scoped>
.container {
  display: flex;
  flex-direction: column;
  align-items: center;
}
</style>