<template>
  <div id="app">
      <div id="header">
          <h1>Space Explorers</h1>
      </div>


      <div id="content">
        <h3>Goals / to do</h3>
        <p>Visual elements that hover / scroll at different speed, and some that
          "float" across seciton boundaries
        </p>

        <p>Spaceship on a path animation</p>
        <p>Load/animate on scroll</p>
        <p>Play Now/Get the App button with special animated popup?</p>
        <p>Visual representation of app somewhere</p>
      </div>
  </div>
</template>

<script>
import Header from "./components/Header";

export default {
  name: "App",
  components: {
    Header
  }
};
</script>

<style>
@import url("https://fonts.googleapis.com/css?family=Bangers|Boogaloo|Carter+One|Fredoka+One|Londrina+Solid|Luckiest+Guy|Righteous|Skranji|Unica+One");
body {
  margin: 0;
  padding: 0;
}

#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
}

h1,
h2,
h3,
h4,
h5 {
  font-family: "Bangers";
  letter-spacing: 1px;
  font-weight: normal;
  margin: 0;
}

#header {
  background: #3b0e5e;
  min-height: 350px;
}

#content {
  padding: 50px;
}

h1 {
  font-size: 70px;
  color: #d13e19;
  text-align: center;
  padding: 10px;
  text-shadow: -1px -1px 0px rgba(255, 255, 255, 0.7),
    1px 1px 1px rgba(0, 0, 0, 0.5);
}
</style>
