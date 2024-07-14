<template>
  <div class="jap-title">
    <div></div>
    <span>{{ text }}</span>
  </div>
</template>

<script>
import gsap from "gsap";
import ScrollTrigger from "gsap/ScrollTrigger";
import SplitText from "gsap/SplitText";

gsap.registerPlugin(ScrollTrigger, SplitText);

export default {
  name: "JapTitle",
  props: {
    text: {
      type: String,
      required: true,
    },
  },
  mounted() {
    const el = this.$el;
    const split = new SplitText(el.querySelector("span"), { type: "chars" });

    gsap.from(split.chars, {
      opacity: 0,
      xPercent: -100,
      duration: 1,
      stagger: 0.05,
      ease: "power2.Out",
      scrollTrigger: {
        trigger: el,
        start: "top 90%", // Démarre l'animation lorsque l'élément est à 80% du viewport
        end: "top 20%", // Termine l'animation lorsque l'élément est à 20% du viewport
      },
    });
  },
};
</script>

<style scoped lang="scss">
@use "/src/styles/variables";

.jap-title {
  display: flex;
  align-items: center;
  gap: 10px;
  & div {
    height: 30px;
    width: 1px;
    background: variables.$red;
    transform: translateY(-2px) rotate(30deg);
  }
  & span {
    color: variables.$red;
    white-space: nowrap;
    font-size: 16px;
    font-weight: 400;
  }
}
</style>
