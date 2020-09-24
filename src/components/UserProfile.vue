<template>
  <div class="userprofile">
    <h1>@{{user.username}}</h1>
    <div class="userpfoile__adminbadge" v-if="user.isAdmin">Admin</div>
    <div class="userpfoile__extradetail">
      {{fullName}}
      <div class="userprofile__followercount">
        <strong>Followers:</strong>
        {{followers}}
      </div>
    </div>
    <button @click="followUser">Follow</button>
    <form class="userprofile__create-tweet" @submit.prevent="createNewTweet">
      <label for="newTweet">
        <b>New Tweet</b>
      </label>
      <textarea id="newTweet" rows="4" v-model="newTweetContent" />
      <button>Tweet</button>
    </form>
  </div>

  <div class="userprofile__tweetswrapper">
    <tweetItem
      v-for="tweet in user.tweets"
      :key="tweet.id"
      :username="user.username"
      :tweet="tweet"
      @favorite="toggleFavorite"
    />
  </div>
</template>

<script>
import TweetItem from "./TweetItem";

export default {
  name: "UserProfile",
  components: { TweetItem },
  data() {
    return {
      newTweetContent: "",
      followers: 0,
      user: {
        id: 1,
        username: "Neo-Dragon",
        firstName: "Stephen",
        lastName: "McVicker",
        email: "mcvickerstephen@gmail.com",
        isAdmin: true,
        tweets: [
          { id: 3, content: "3rd tweet just for more content." },
          { id: 2, content: "Another tweet here..." },
          { id: 1, content: "Twitter is amazing!" },
        ],
      },
    };
  },
  computed: {
    fullName() {
      return `${this.user.firstName} ${this.user.lastName}`;
    },
  },
  methods: {
    followUser() {
      this.followers++;
    },
    toggleFavorite(id) {
      console.log("Favorited tweet" + id);
    },
    createNewTweet() {
      // Make sure there is content
      if (this.newTweetContent.length <= 0) {
        console.log("No content in textfield");
        return;
      }

      // Add the tweet
      this.user.tweets.unshift({
        id: this.user.tweets.length + 1,
        content: this.newTweetContent,
      });

      // Reset textbox content
      this.newTweetContent = "";
    },
  },
  // Example of lifecycle method
  mounted() {
    console.log("UserProfile mounted...");
  },

  // Example of way to do something on data change
  watch: {
    followers(newFollowerCount, oldFollowerCount) {
      if (oldFollowerCount < newFollowerCount) {
        console.log(`${this.user.username} has gained a follower!`);
      }
    },
  },
};
</script>

<style>
.userprofile {
  width: 300px;
  padding: 2em;
  margin: 1em;
  background-color: #d6eedd;
  border-radius: 10px;

  display: flex;
  flex-direction: column;
  text-align: left;

  align-self: start;

  box-shadow: 0 2px 4px 0px #3d4f5241;
}

.userpfoile__adminbadge {
  background-color: #eb3b98;
  border-radius: 50vh;
  color: white;
  padding: 0.2em 1em;
  margin-right: auto;
  margin-bottom: 1em;
}

.userpfoile__extradetail {
  display: flex;
  flex-direction: row;
  justify-content: space-between;
}

.userprofile__create-tweet {
  margin-top: 1em;
  border-top: 1px solid #41b883;
  padding-top: 1em;
  display: flex;
  flex-direction: column;
}

.userprofile__tweetswrapper {
  min-width: 50%;
}

@media only screen and (max-width: 768px) {
  .userprofile__tweetswrapper {
    width: 100%;
  }
}

h1 {
  margin-top: 0px;
  color: #41b883;
}

button {
  padding: 0.8em 1em;
  margin-top: 1em;

  display: inline-flex;
  justify-content: center;
  align-items: center;

  border-radius: 16px;
  border: none;
  outline: none;

  text-transform: uppercase;
  font-weight: bold;
  background-color: #41b883;
  color: white;

  cursor: pointer;

  transition: all 0.2s;
}

button:active {
  transform: scale(0.96);
}
</style>