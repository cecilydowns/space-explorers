<template>
  <div id="app">

      <div id="spaceship">
         <img src="./assets/spaceship.svg" />
      </div>


      <Header/>

      <div id="button">
        Get the App
      </div>

      <div id="content">

        <div id="phone">
          <img src="./assets/phone.png" />
        </div>
        <h2>Goals / to do</h2>
        <p>Visual elements that hover / scroll at different speed, and some that
          "float" across seciton boundaries
        </p>


        <p> Content area: text on left, phone image on right.</p>

        <p>Play Now/Get the App button with special animated popup?</p>
        <p>Three-column features list</p>


        <p>Dark footer with large orange planet below everything else? </p>


        <a href='https://www.freepik.com/free-vector/fantastic-galaxy-background-with-purple-lights_930794.htm'>Space Background: Freepix</a>
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
  font-family: "Righteous";
  letter-spacing: 1px;
  font-weight: normal;
  margin: 0;
}

#button {
  position: absolute;
  right: 20px;
  margin-top: -40px;
  padding: 15px;
  background: yellow;
  border-radius: 10px;
  box-shadow: 1px 1px 5px rgba(0, 0, 0, 0.2);
}

#spaceship {
  width: 80px;
  height: 80px;
  position: absolute;
  right: 10px;
  top: 200px;
  z-index: 10;
}

#content {
  padding: 50px;
}

#phone {
  float: right;
}

#phone img {
  max-width: 250px;
}
</style>
