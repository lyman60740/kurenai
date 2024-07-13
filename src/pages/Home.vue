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
import jsonData from "../data/data.json";

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
    return {
      sectionData: jsonData.sections[0], // Prend la première section de votre JSON
      contactInfo: jsonData.contactInfo,
    };
  },
  mounted() {
    // Ici, vous pouvez utiliser GSAP pour des animations si nécessaire
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
