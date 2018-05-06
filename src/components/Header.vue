<template>
    <div id="header">
      <div class="background">
        <img src="../assets/star.svg" class="star star-small" id="star-1" />
        <img src="../assets/star.svg" class="star star-medium" id="star-2" />
        <img src="../assets/star.svg" class="star star-large" id="star-3" />
        <img src="../assets/star.svg" class="star star-small" id="star-4" />
        <img src="../assets/star.svg" class="star star-medium" id="star-5" />
        <img src="../assets/star.svg" class="star star-large" id="star-6" />

        <img src="../assets/meteor.svg" id="meteor">
        <img src="../assets/meteor2.svg" id="meteor-2">

        <img src="../assets/ringplanet.svg" id="planet-1">
        <img src="../assets/ringplanet2.svg" id="planet-2">
        <img src="../assets/cloudplanet.svg" id="planet-3">


        </div>
        <h1>Space<br>Explorers</h1>

      <div id="features">
        <div class="feature">
          <h3>Choose Your Starship!</h3>
         <p>Lorem ipsum dolor sit amet, consectetur adipiscing elit. Duis elementum leo et ipsum accumsan, ac viverra dui lobortis.</p>
        </div>

        <div class="feature">
                    <h3>Visit Alien Worlds!</h3>
                             <p> maecenas sed tincidunt dolor.</p>
        </div>

        <div class="feature">
                    <h3>A Galaxy Awaits!</h3>
         <p>Maecenas sed tincidunt dolor. Nulla facilisi. Proin elementum urna non libero tempus maximus.</p>
        </div>
      </div>

  </div>

</template>

<script>
export default {
  name: "Header",
  data() {
    return {
      msg: "Welcome to Your Vue.js App"
    };
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
#header {
  background: #002535;
  background-image: linear-gradient(#002535, rgb(50, 0, 50));
  /* background-image: url("./assets/spacebg.jpg"); */
  background-size: cover;
  height: 550px;
  -webkit-clip-path: polygon(0 0, 2000px 0, 2000 87%, 0 100%);
  clip-path: polygon(0 0, 2000px 0, 2000px 87%, 0 100%);
}

h1 {
  font-size: 55px;
  color: #f47920;
  text-align: center;
  padding: 40px 10px;
  text-shadow: -1px -1px 0px#F79C1F, 1px 1px 0px rgba(0, 0, 0, 1),
    2px 2px 15px rgba(0, 0, 0, 0.7);
  transform: skew(0deg, -6deg);
  line-height: 45px;
  z-index: 10;
}

#features {
  padding: 50px;
  margin-right: -1%;
}

.feature {
  box-sizing: border-box;
  width: 31%;
  float: left;
  padding: 15px;
  margin: 1%;
  background: rgba(100, 0, 100, 0.2);
  color: #fff;
  /* -webkit-clip-path: polygon(0 0, 600px 0, 600 87%, 0 100%);
  clip-path: polygon(0 0, 600px 0, 600px 87%, 0 100%); */

  -webkit-clip-path: polygon(0 6%, 100% 0%, 100% 94%, 0% 100%);
  clip-path: polygon(0 6%, 100% 0%, 100% 94%, 0% 100%);
}

.feature:hover {
  transform: scale(1.05);
}

.feature h3 {
  font-size: 30px;
  transform: skew(0deg, -3deg);
  line-height: 25px;
  font-family: "Carter One";
  color: yellow;
}

.background {
  z-index: 1;
}

.background img {
  position: absolute;
}

.star {
  animation: twinkle 5s infinite alternate;
  opacity: 0.8;
}

.star-small {
  width: 15px;
}

.star-medium {
  width: 25px;
}

.star-large {
  width: 35px;
}

#star-1 {
  left: 20%;
  top: 50px;
  animation-delay: 0.5s;
}

#star-2 {
  right: 10%;
  top: 20px;
}

#star-3 {
  left: 5%;
  top: 60px;
  animation-delay: 1.5s;
}
#star-4 {
  left: 9%;
  top: 150px;
  animation-delay: 2.5s;
}
#star-5 {
  right: 17%;
  top: 170px;
}
#star-6 {
  left: 45%;
  top: 150px;
  animation-delay: 3.5s;
}

#meteor {
  width: 120px;
  left: -120px;
  top: 40px;
  transform: rotate(50deg);
  animation: shoot 10s 4s infinite;
}

#meteor-2 {
  width: 80px;
  transform: rotate(280deg);
  right: -100px;
  animation: shoot2 14s 7s infinite;
}

#planet-1 {
  width: 80px;
  right: 20%;
  top: 50px;
}

#planet-2 {
  width: 80px;
  left: 15%;
  top: 160px;
}

#planet-3 {
  width: 60px;
  right: 35%;
  top: 190px;
}

@keyframes twinkle {
  0% {
    transform: scale(1);
    opacity: 0.8;
  }
  100% {
    transform: scale(1.2) rotate(2deg);
    opacity: 1;
  }
}

@keyframes shoot {
  0% {
    transform: rotate(50deg);
  }

  25% {
    transform: translateX(1600px) translateY(1400px) rotate(50deg);
  }

  100% {
    transform: translateX(1600px) translateY(1400px) rotate(50deg);
  }
}

@keyframes shoot2 {
  0% {
    transform: rotate(280deg);
  }

  20% {
    transform: translateX(-1800px) translateY(800px) rotate(270deg);
  }

  100% {
    transform: translateX(-1800px) translateY(800px) rotate(270deg);
  }
}
</style>
