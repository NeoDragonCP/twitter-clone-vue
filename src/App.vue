<template>
  <div id="app">
    <nav>
      <div class="header">Twitter</div>
    </nav>
    <div class="content-wrapper">
      <UserProfile />
    </div>
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
body {
  padding: 0;
  margin: 0;
  overflow-x: hidden;
  display: flex;
  flex-direction: column;
}

#app {
  width: 100vw;

  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;

  color: #2c3e50;
}

.header {
  padding: 1em 2em;
  background-color: #41b883;
  color: white;
  font-weight: bold;
  font-size: 1.2em;
}

.content-wrapper {
  display: flex;
  flex-direction: row;
  align-items: space;
  justify-content: space-evenly;
  text-align: center;
}

@media only screen and (max-width: 768px) {
  .content-wrapper {
    height: auto;
    margin: 0;
    padding: 1em;
    flex-direction: column;
    justify-content: center;
    align-items: center;
  }
}
</style>
