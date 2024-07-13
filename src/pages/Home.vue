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

<style scoped lang="scss">
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
</style>
