<template>
  <div class="tweet-item" @click="favoritetweet(tweet.id)">
    <div class="user-profile__tweet">
      <div class="tweet-item__user">@{{username}}</div>
      <div class="tweet-item__content">{{tweet.content}}</div>
    </div>
  </div>
</template>

<script>
export default {
  name: "tweetItem",
  props: {
    username: {
      type: String,
      required: true,
    },
    tweet: {
      type: Object,
      required: true,
    },
  },
  methods: {
    favoritetweet(id) {
      this.$emit("favorite", id);
    },
  },
};
</script>

<style scopped>
.tweet-item {
  margin: 1em;
  padding: 2em;
  background-color: white;
  border-radius: 6px;
  border: 1px solid #41b883;
  cursor: pointer;

  word-wrap: break-word;

  box-shadow: 0 2px 4px 0px #3d4f5241;

  transition: all 0.3s ease;
}

.tweet-item:hover {
  transform: scale(1.1);
}

.tweet-item__user {
  color: #41b883;
  font-weight: bold;
  margin-bottom: 1em;
}
</style>