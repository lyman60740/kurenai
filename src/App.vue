<template>
  <NavBar />
  <div id="smooth-wrapper">
    <div id="smooth-content">
      <Home />
      <Footer />
    </div>
  </div>
</template>

<script>
import Home from "./pages/Home.vue";
import NavBar from "./components/NavBar.vue";
import Footer from "./components/Footer.vue";

import gsap from "gsap";
import ScrollTrigger from "gsap/ScrollTrigger";
import ScrollSmoother from "gsap/ScrollSmoother";

gsap.registerPlugin(ScrollTrigger, ScrollSmoother);

window.addEventListener("beforeunload", function () {
  window.scrollTo(0, 0);
});

export default {
  name: "App",
  components: {
    Home,
    NavBar,
    Footer,
  },
  data() {
    return {};
  },
  mounted() {
    ScrollSmoother.create({
      smooth: 1,
      effects: true,
      smoothTouch: 0.1,
    });
  },
};
</script>

<style scoped></style>
