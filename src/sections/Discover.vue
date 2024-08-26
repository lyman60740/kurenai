<template>
  <section class="discover" data-section-id="section2">
    <h2>
      <span style="text-align: center">Discover our menus and</span>
      <span style="text-align: left">indulge in an unforgettable</span>
      <span style="text-align: right">gastronomic experience,</span>
      <span style="text-align: left">combining culinary flavors</span>
      <span style="text-align: center">and refined cocktails.</span>
    </h2>
  </section>
</template>

<script>
import gsap from "gsap";
import ScrollTrigger from "gsap/ScrollTrigger";
gsap.registerPlugin(ScrollTrigger);

export default {
  name: "Discover",
  components: {},
  data() {
    return {};
  },
  mounted() {
    const spans = this.$el.querySelectorAll("span");

    const tl = gsap.timeline({
      scrollTrigger: {
        trigger: ".discover",
        start: "center center",
        end: "bottom top",
        scrub: true,
        pin: true,
      },
    });

    spans.forEach((span, index) => {
      const direction = index % 2 === 0 ? -100 : 100; // Alternates direction
      tl.from(
        span,
        {
          x: direction,
          opacity: 0,
          duration: 1,
          ease: "power1.out",
        },
        `-=${0.5}`
      );
    });
  },
};
</script>

<style scoped lang="scss">
@use "/src/styles/variables";

.discover {
  display: flex;
  justify-content: center;
  align-items: center;
  position: relative;
  & h2 {
    display: flex;
    flex-direction: column;
    font-family: variables.$bigilla;
    font-size: 80px;
    font-weight: bold;
    color: variables.$red;
    width: 90%;
    max-width: 1200px;
  }
}
@media screen and (max-width: 900px) {
  .discover h2 {
    font-size: 7.5vw;
    justify-content: space-between;
    height: 70%;
  }
  .events__bandeau span {
    font-size: 15vw;
  }
}
</style>
