<template>
  <main>
    <Header />
    <div class="large-container">
      <div class="main-container">
        <Intro />
      </div>
      <FullScreen />
      <div class="main-container">
        <Culture />
        <Discover />
      </div>
      <Events />
    </div>
    <div class="slideButton">
      <svg
        width="32"
        height="16"
        viewBox="0 0 32 16"
        fill="none"
        xmlns="http://www.w3.org/2000/svg"
      >
        <path
          d="M0 8H32M32 8C27.5817 8 24 4.41828 24 0M32 8C27.5817 8 24 11.5817 24 16"
          stroke="#B50B0C"
        />
      </svg>
    </div>
    <div class="ourmenu-button">
      <span
        >OUR<br />
        MENU</span
      >
      <svg
        width="32"
        height="16"
        viewBox="0 0 32 16"
        fill="none"
        xmlns="http://www.w3.org/2000/svg"
      >
        <path
          d="M0 8H32M32 8C27.5817 8 24 4.41828 24 0M32 8C27.5817 8 24 11.5817 24 16"
          stroke="#B50B0C"
        />
      </svg>
    </div>
  </main>
</template>

<script>
import gsap from "gsap";
import ScrollTrigger from "gsap/ScrollTrigger";

gsap.registerPlugin(ScrollTrigger);

import Header from "../sections/Header.vue";
import Intro from "../sections/Intro.vue";
import FullScreen from "../sections/FullScreen.vue";
import Culture from "../sections/Culture.vue";
import Discover from "../sections/Discover.vue";
import Events from "../sections/Events.vue";

export default {
  name: "Hero",
  components: {
    Header,
    Intro,
    FullScreen,
    Culture,
    Discover,
    Events,
  },
  data() {
    return {};
  },
  mounted() {
    gsap.utils.toArray(".img-parallax").forEach((element) => {
      gsap.to(element, {
        backgroundPosition: "50% 50%",
        ease: "none",
        scrollTrigger: {
          trigger: element,
          start: "top bottom",
          end: "bottom top",
          scrub: true,
          onUpdate: (self) => {
            const progress = self.progress * 100;
            element.style.backgroundPosition = `50% ${progress}%`;
          },
        },
      });
    });
  },
};
</script>

<style lang="scss">
@use "/src/styles/variables";
.large-container {
  width: 100%;
  background: variables.$white;
  position: relative;
  z-index: 5;
}
.hero {
  width: 100%;
  height: 100%;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  & h1 {
    font-size: 3rem;
    margin-bottom: 20px;
  }
  & p {
    margin: 0px 0 50px 0;
  }
}
.main-container {
  background: variables.$white;
  position: relative;
}
.slideButton {
  border: 1px solid variables.$red;
  position: fixed; /* Fixe par rapport au viewport */
  pointer-events: none; /* S'assure que l'élément ne bloque pas les événements de la souris */
  transform: translate(-50%, -50%);
  top: 0;
  left: 0;
  opacity: 0;

  height: 175px;
  width: 175px;
  border-radius: 50%;
  display: flex;
  align-items: center;
  justify-content: center;
  will-change: transform;
  // transition: transform 0.1s ease-out;
  z-index: 15;
}
.ourmenu-button {
  height: 175px;
  width: 175px;
  border-radius: 50%;
  display: flex;
  align-items: center;
  justify-content: center;
  flex-direction: column;
  gap: 16px;
  will-change: transform;
  position: fixed;
  pointer-events: none;
  transform: translate(-50%, -50%);
  top: 0;
  left: 0;
  opacity: 0;
  z-index: 15;
  background: variables.$red;
  & span {
    font-size: 20px;
    font-weight: 300;
    text-transform: uppercase;
    line-height: 30px;
    text-align: center;
    color: variables.$white;
    transform: translateY(15%);
  }
}
</style>
