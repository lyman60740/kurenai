<template>
  <section class="culture" data-section-id="section1">
    <div class="culture__title">
      <span>Savor the art of</span>
      <h1>/ Japanese Cocktails</h1>
    </div>
    <p>
      Step into a world where Japanese tradition and innovation converge in
      every glass. Our cocktails, infused with unique Japanese flavors, are
      paired with delightful small plates to enhance your experience. Allow our
      expertise to guide you through drinks that tell a story.
    </p>
    <div
      data-speed="0.9"
      class="grid-img-left culture__img1 hoverCursorElement img-parallax"
    >
      <JapTitle text="カクテル" />
    </div>

    <div
      data-speed="1.1"
      class="grid-img-right culture__img2 hoverCursorElement img-parallax"
    >
      <JapTitle text="カクテル" />
    </div>

    <div
      data-speed="0.9"
      class="grid-img-right culture__img3 hoverCursorElement img-parallax"
    >
      <JapTitle text="カクテル" />
    </div>
    <div
      data-speed="1.1"
      class="grid-img-left culture__img4 hoverCursorElement img-parallax"
    >
      <JapTitle text="カクテル" />
    </div>
  </section>

  <section class="culture bis">
    <div class="culture__title">
      <span>Awaken your senses with our</span>
      <h2>/ Japanese cuisine</h2>
    </div>
    <p>
      Step into a world where Japanese tradition and innovation converge in
      every glass. Our cocktails, infused with unique Japanese flavors, are
      paired with delightful small plates to enhance your experience. Allow our
      expertise to guide you through drinks that tell a story.
    </p>
    <div data-speed="0.9" class="grid-img-right culture__img1 img-parallax">
      <JapTitle text="カクテル" />
    </div>
    <div
      data-speed="1.1"
      class="grid-img-left culture__img2 hoverCursorElement img-parallax"
    >
      <JapTitle text="カクテル" />
    </div>

    <div
      data-speed="1.1"
      class="grid-img-left culture__img3 hoverCursorElement img-parallax"
    >
      <JapTitle text="カクテル" />
    </div>
    <div
      data-speed="0.9"
      class="grid-img-right culture__img4 hoverCursorElement img-parallax"
    >
      <JapTitle text="カクテル" />
    </div>
  </section>
</template>

<script>
import gsap from "gsap";
import ScrollTrigger from "gsap/ScrollTrigger";
gsap.registerPlugin(ScrollTrigger);

import JapTitle from "../components/JapTitle.vue";

export default {
  name: "Culture",
  components: {
    JapTitle,
  },
  data() {
    return {
      mouseX: 0,
      mouseY: 0,
    };
  },
  mounted() {
    gsap.to(".culture__title span", {
      y: 0,
      scrollTrigger: {
        trigger: ".culture",
        start: "top bottom",
        end: "top+=30vh top",
        scrub: true,
      },
    });

    gsap.to(".culture__title span", {
      color: "#B50B0C",
      scrollTrigger: {
        trigger: ".culture",
        start: "top+=250 bottom",
        end: "top+=400 bottom",
        scrub: true,
      },
    });

    // document.querySelectorAll(".culture").forEach((element) => {
    //   const discoverElement = document.querySelector(".discover-button");

    //   element.addEventListener("mouseenter", (e) => {
    //     this.mouseX = e.pageX;
    //     this.mouseY = e.pageY;

    //     gsap.set(discoverElement, {
    //       y: this.mouseY + "px",
    //       x: this.mouseX + "px",
    //     });
    //   });

    //   element.addEventListener("mousemove", (e) => {
    //     this.mouseX = e.pageX;
    //     this.mouseY = e.pageY;

    //     gsap.to(discoverElement, {
    //       y: this.mouseY + 90 + "px",
    //       x: this.mouseX + 90 + "px",
    //       duration: 0.8,
    //       ease: "power3.out",
    //       overwrite: "auto",
    //     });
    //   });
    // });

    document.querySelectorAll(".hoverCursorElement").forEach((element) => {
      element.addEventListener("mouseenter", (e) => {
        gsap.fromTo(
          ".discover-button",
          {
            border: "1px solid #B50B0C",
            autoAlpha: 0,
          },
          {
            border: "1px solid #FFF8E8",
            autoAlpha: 1,
          }
        );
        gsap.to(".discover-button span", {
          color: "#FFF8E8",
        });
        gsap.to(".discover-button svg path", {
          fill: "#FFF8E8",
          stroke: "#FFF8E8",
        });
      });

      element.addEventListener("mouseleave", (e) => {
        gsap.fromTo(
          ".discover-button",
          {
            border: "1px solid #FFF8E8",
            autoAlpha: 1,
          },
          {
            border: "1px solid #B50B0C",
            autoAlpha: 0,
          }
        );
        gsap.to(".discover-button span", {
          color: "#B50B0C",
        });
        gsap.to(".discover-button svg path", {
          fill: "#B50B0C",
          stroke: "#B50B0C",
        });
      });
    });
  },
};
</script>

<style scoped lang="scss">
@use "/src/styles/variables";
.culture {
  display: grid;
  grid-template-columns: repeat(12, 1fr); /* 12 colonnes de largeur égale */
  grid-template-rows: repeat(28, 1fr); /* 12 colonnes de largeur égale */
  gap: 24px; /* Espacement entre les colonnes */
  width: 100%;
  max-width: 1600px;
  margin: 0 auto;
  box-sizing: border-box;
  position: relative;
  &__title {
    grid-column: 1 / span 12;
    grid-row: 2 / span 4;
    display: flex;
    flex-direction: column;
    & span {
      font-family: variables.$bigilla;
      font-size: 131px;
      font-weight: bold;
      color: variables.$red;
      align-self: flex-end;
      transform: translateY(-40vh);
      color: variables.$white;
    }
    & h1 {
      font-family: variables.$bigilla;
      font-size: 131px;
      font-weight: bold;
      color: variables.$red;
    }
  }
  & p {
    grid-column: 10 / span 4;
    grid-row: 7 / span 2;
    text-indent: 2em;
  }
  &__img1 {
    grid-column: 2 / span 5;
    grid-row: 9 / span 7;
    background-image: url("/src/assets/header.webp");
    background-size: 210%;
    background-position: 50% 50%;
  }
  &__img2 {
    grid-column: 9 / span 4;
    grid-row: 14 / span 4;
    background-image: url("/src/assets/header.webp");
    background-size: 160%;
    background-position: 50% 50%;
  }
  &__img3 {
    grid-column: 4 / span 10;
    grid-row: 20 / span 6;
    background-image: url("/src/assets/header.webp");
    transform: translateX(30%);
    background-size: 110%;
    background-position: 50% 50%;
  }
  &__img4 {
    grid-column: 2 / span 3;
    grid-row: 24 / span 4;
    background-image: url("/src/assets/header.webp");
    background-size: 230%;
    background-position: 50% 50%;
  }
}
.hoverCursorElement {
  cursor: pointer;
}
.bis {
  & .culture__title {
    & span {
      align-self: flex-start !important;
    }
    & h2 {
      font-family: variables.$bigilla;
      font-size: 131px;
      font-weight: bold;
      color: variables.$red;
      align-self: flex-end !important;
    }
  }
  & p {
    grid-column: 2 / span 4;
  }
  & .culture__img1 {
    grid-column: 7 / span 5;
    grid-row: 9 / span 7;
    background-image: url("/src/assets/header.webp");
    background-size: 190%;
    background-position: 50% 50%;
  }
  & .discover-button {
    grid-column: 3 / span 2;
    grid-row: 11 / span 2;
  }
  & .culture__img2 {
    grid-column: 2 / span 4;
    background-size: 140%;
    background-position: 50% 50%;
  }
  & .culture__img3 {
    grid-column: 1 / span 10;
    transform: translateX(-30%);
    background-size: 100%;
    background-position: 50% 50%;
  }
  & .culture__img4 {
    grid-column: 9 / span 4;
    background-size: 140%;
    background-position: 50% 50%;
  }
}
</style>
