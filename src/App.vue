<template>
  <div id="app">
    <UserProfile />
  </div>
</template>

<script>
import UserProfile from "./components/UserProfile";

export default {
  name: "App",
  components: { UserProfile },
};
</script>

<style>
#app {
  width: 100vw;
  height: 100vh;

  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;

  color: #2c3e50;

  display: flex;
  flex-direction: row;
  align-items: space;
  justify-content: space-evenly;
  text-align: center;
}

@media only screen and (max-width: 768px) {
  #app {
    margin: 0;
    padding: 1em;
    flex-direction: column;
    justify-content: center;
    align-items: center;
  }
}
</style>
