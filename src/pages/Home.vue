<template>
  <main>
    <Header />
    <div class="main-container">
      <Intro />
    </div>
    <FullScreen />
    <div class="main-container">
      <Culture />
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

export default {
  name: "Hero",
  components: {
    Header,
    Intro,
    FullScreen,
    Culture,
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
  width: 100%;
  max-width: 1600px;
  margin: 0 auto;
  box-sizing: border-box;
}
</style>
