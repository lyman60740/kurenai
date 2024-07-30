<template>
  <section class="intro">
    <div class="intro__content">
      <JapTitle text="クレナイへようこそ" />
      <h3>
        Step into Kurenai, where elegance and Japanese tradition converge in an
        immersive deep red ambiance.
      </h3>
      <p>
        Step into Kurenai, where elegance and Japanese tradition converge in an
        immersive deep red ambiance. Located on an iconic site in Chinatown, our
        bar-restaurant is a hub of cultural renaissance that blends culinary art
        with a unique sensory experience. Come to discover our story and savor
        every moment in an unforgettable setting.
      </p>
      <a href="#" class="intro__content__read-more">
        <img
          class="arrow-animate"
          src="/src/assets/arrow.svg"
          alt="arrow icon"
        />
        <span>Read more</span>
        <img
          class="arrow-animate-out"
          src="/src/assets/arrow.svg"
          alt="arrow icon"
        />
      </a>
    </div>

    <div
      class="intro__img1 img-parallax"
      data-speed="0.8"
      speed-parralax="1"
    ></div>
    <div
      class="intro__img2 img-parallax"
      data-speed="1"
      speed-parralax="1"
    ></div>

    <div class="intro__adress">
      <div>
        <p>123 Fake Street</p>
        <p>London W1D 5PT • UK</p>
      </div>
      <div>
        <p>00 000 000 00</p>
      </div>
      <div>
        <p>Mon — Fri • 11:30 — 19:00</p>
        <p>Sat — Sun • 14:00 — 21:00</p>
      </div>
    </div>
  </section>
</template>

<script>
import gsap from "gsap";

import JapTitle from "../components/JapTitle.vue";

export default {
  name: "Intro",
  components: {
    JapTitle,
  },
  data() {
    return {};
  },
  mounted() {
    const readMore = document.querySelectorAll(".intro__content__read-more");

    readMore.forEach((el) => {
      const arrow = el.querySelector(".arrow-animate");
      const arrowOut = el.querySelector(".arrow-animate-out");
      const spans = el.querySelector("span");

      el.addEventListener("mouseenter", () => {
        const tl = gsap.timeline();
        tl.to(arrowOut, {
          duration: 0.3,
          x: 50,
          autoAlpha: 0,
          ease: "power2.in",
        })
          .to(arrow, {
            duration: 0.3,
            x: 0,
            autoAlpha: 1,
            ease: "power2.Out",
          })
          .to(
            spans,
            {
              duration: 0.3,
              x: 50,
              ease: "power2.Out",
            },
            "<"
          );
      });
      el.addEventListener("mouseleave", () => {
        const tl = gsap.timeline();
        tl.to(arrow, {
          duration: 0.3,
          x: -50,
          autoAlpha: 0,
          overwrite: "auto",
        })
          .to(
            spans,
            {
              duration: 0.3,
              x: 0,
              overwrite: "auto",
            },
            "<"
          )
          .to(arrowOut, {
            duration: 0.3,
            x: 0,
            autoAlpha: 1,
            overwrite: "auto",
          });
      });
    });
  },
};
</script>

<style scoped lang="scss">
@use "/src/styles/variables";
.intro {
  display: grid;
  grid-template-columns: repeat(12, 1fr); /* 12 colonnes de largeur égale */
  grid-template-rows: repeat(14, 1fr); /* 12 colonnes de largeur égale */
  gap: 24px; /* Espacement entre les colonnes */
  background: variables.$white;
  &__content {
    grid-column: 7 / span 6;
    grid-row: 2 / span 4;
    display: flex;
    flex-direction: column;
    justify-content: center;
    gap: 80px;
    & h3 {
      font-family: variables.$bigilla;
      font-size: 40px;
      font-weight: bold;
      color: variables.$red;
    }
    &__read-more {
      align-self: flex-end;
      display: flex;
      gap: 24px;
      align-items: center;
      position: relative;
      overflow: hidden;
      & span {
        font-size: 20px;
        color: variables.$red;
        font-weight: 500;
        text-transform: uppercase;
        letter-spacing: 1.2px;
      }
    }
  }
  &__img1 {
    background-image: url("/src/assets/intro_img1.png");
    background-size: 140%;
    background-position: 50% 20%;
    grid-column: 1 / span 3;
    grid-row: 4 / span 4;
  }
  &__img2 {
    background-image: url("/src/assets/intro_img2.png");
    background-size: 140%;
    background-position: 50% 10%;
    grid-column: 8 / span 6;
    grid-row: 7 / span 6;
  }
  &__adress {
    grid-column: 1 / span 2;
    grid-row: 12 / span 2;
    display: flex;
    flex-direction: column;
    border-top: 1px solid variables.$red;
    padding-top: 40px;
    box-sizing: border-box;
    gap: 40px;
    & div {
      display: flex;
      flex-direction: column;
      width: max-content;
      & p {
        font-size: 20px;
        font-weight: 400;
        color: variables.$red;
        width: max-content;
      }
    }
  }
}

.arrow-animate {
  position: absolute;
  top: 50%;
  left: 0;
  transform: translate(-50px, -50%);
}
</style>
