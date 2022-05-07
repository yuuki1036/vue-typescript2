<script setup lang="ts">
import { defineProps } from 'vue';

type Tweet = {
  id: number,
  desc: string,
}

type Props = {
  tweets: Tweet[]
}

defineProps<Props>()

const emit = defineEmits(["delete-tweet"])
const deleteTweet = (id:number) => {
  emit("delete-tweet", id)
}

</script>

<template>
  <div class="tweet-container">
    <p v-if="tweets.length <= 0">no tweets</p>
    <ul v-else>
      <li v-for="tweet in tweets" :key="tweet.id" class="tweet-list">
        <span>{{ tweet.desc }}</span>
        <button class="delete-button" @click="deleteTweet(tweet.id)">Delete</button>
      </li>
    </ul>
  </div>
</template>

<style scoped>
.tweet-list {
  list-style: none;
  margin-bottom: 12px;
  border-radius: 4px;
  font-size:12px;
  display: flex;
  justify-content: space-between;
  background-color: azure;
  padding: 8px 20px;
  width:300px;
}
.delete-button {
  color: #fff;
  font-weight: bold;
  background-color: #c99a68;
  border-radius: 2px;
  border:none;
  width: 60px;
  height: 22px;
}

</style>