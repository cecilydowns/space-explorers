<template>
   <div id="background">
      <Star size=20 left="20%" top="50px" delay=0.5 duration=5 />
      <Star size=15 right="10%" top="20px" delay=0.2 duration=4 />
      <Star size=22 left="5%" top="20px" delay=1 duration=6 />
      <Star size=15 left="9%" top="150px" delay=2.5 duration=5 />
      <Star size=25 right="17%" top="170px" delay=0 duration=5 />
      <Star size=25 left="45%" top="150px" delay=3.5 duration=5 />
      <Star size=25 left="40%" bottom="40px" delay=3.5 duration=5 />
      <Star size=20 left="30%" bottom="60px" delay=.5 duration=3 />
      <Star size=28 left="60%" bottom="80px" delay=.5 duration=4 />
      <Star size=35 left="60%" top="53%" delay=.5 duration=4 />

      <Rock size="30" top="275px" left="3%" type=5 />
      <Rock size="30" top="70px" left="85%" type=2 />
      <Rock size="20" top="140px" left="15%" type=1 />
      <Rock size="40" bottom="150px" left="15%" type=4 />

      <img src="../assets/meteor.svg" id="meteor">
      <img src="../assets/meteor2.svg" id="meteor-2">
   </div>
</template>

<script>
import Star from "./Star";
import Rock from "./Rock";

export default {
  name: "Background",
  components: {
    Star,
    Rock
  }
};
</script>

<style scoped>
#background {
  position: fixed;
  top: 0;
  left: 0;
  width: 100vw;
  height: 100vh;
  background: #002535;
  background-size: cover;
  background-image: linear-gradient(#002535, rgb(50, 0, 50));
  overflow: hidden;
  z-index: -1;
}

#background img {
  position: absolute;
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
