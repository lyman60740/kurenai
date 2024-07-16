<template>
  <section class="discover">
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

    const eventBox = document.querySelector(".discover h2");
    const slideButton = document.querySelector(".ourmenu-button");

    const throttle = (func, limit) => {
      let lastFunc;
      let lastRan;
      return function () {
        const context = this;
        const args = arguments;
        if (!lastRan) {
          func.apply(context, args);
          lastRan = Date.now();
        } else {
          clearTimeout(lastFunc);
          lastFunc = setTimeout(function () {
            if (Date.now() - lastRan >= limit) {
              func.apply(context, args);
              lastRan = Date.now();
            }
          }, limit - (Date.now() - lastRan));
        }
      };
    };

    const handleMouseMove = (e) => {
      this.mouseX = e.clientX;
      this.mouseY = e.clientY;

      gsap.to(slideButton, {
        y: this.mouseY + window.scrollY + 90 + "px",
        x: this.mouseX + 90 + "px",
        duration: 0.8,
        ease: "power3.out",
        overwrite: "auto",
      });
    };

    const throttledMouseMove = throttle(handleMouseMove, 100);

    eventBox.addEventListener("mousemove", throttledMouseMove);

    eventBox.addEventListener("mouseenter", (e) => {
      this.mouseX = e.clientX;
      this.mouseY = e.clientY;

      gsap.set(slideButton, {
        y: this.mouseY + window.scrollY + "px",
        x: this.mouseX + "px",
      });

      gsap.fromTo(
        slideButton,
        {
          opacity: 0,
        },
        {
          opacity: 1,
          duration: 0.5, // Ajout de la durée pour l'animation d'entrée
          ease: "power2.out",
          overwrite: "auto",
        }
      );
    });

    eventBox.addEventListener("mouseleave", (e) => {
      this.mouseX = e.clientX;
      this.mouseY = e.clientY;

      gsap.set(slideButton, {
        y: this.mouseY + window.scrollY + "px",
        x: this.mouseX + "px",
      });

      gsap.fromTo(
        slideButton,
        {
          opacity: 1,
        },
        {
          opacity: 0,
          duration: 0.5, // Ajout de la durée pour l'animation de sortie
          ease: "power2.out",
          overwrite: "auto",
        }
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
</style>
