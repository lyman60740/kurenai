<template>
  <section class="culture">
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
    <div class="grid-img-left culture__img1">
      <JapTitle text="カクテル" />
    </div>
    <button class="discover">
      <span
        >Discover <br />
        bar</span
      >
      <img src="/src/assets/arrow.svg" alt="arrow icon" />
    </button>
    <div class="grid-img-right culture__img2">
      <JapTitle text="カクテル" />
    </div>

    <div class="grid-img-right culture__img3">
      <JapTitle text="カクテル" />
    </div>
    <div class="grid-img-left culture__img4">
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
    <div class="grid-img-right culture__img1">
      <JapTitle text="カクテル" />
    </div>
    <button class="discover">
      <span
        >Discover <br />
        bar</span
      >
      <img src="/src/assets/arrow.svg" alt="arrow icon" />
    </button>
    <div class="grid-img-left culture__img2">
      <JapTitle text="カクテル" />
    </div>

    <div class="grid-img-left culture__img3">
      <JapTitle text="カクテル" />
    </div>
    <div class="grid-img-right culture__img4">
      <JapTitle text="カクテル" />
    </div>
  </section>
</template>

<script>
import gsap from "gsap";

import JapTitle from "../components/JapTitle.vue";

export default {
  name: "Culture",
  components: {
    JapTitle,
  },
  data() {
    return {};
  },
  mounted() {
    // Ici, vous pouvez utiliser GSAP pour des animations si nécessaire
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
  }
  & .discover {
    grid-column: 9 / span 2;
    grid-row: 11 / span 2;
    border: 1px solid variables.$red;
    cursor: pointer;
    & span {
      color: variables.$red;
    }
  }
  &__img2 {
    grid-column: 9 / span 4;
    grid-row: 14 / span 4;
    background-image: url("/src/assets/header.webp");
  }
  &__img3 {
    grid-column: 4 / span 10;
    grid-row: 20 / span 6;
    background-image: url("/src/assets/header.webp");
    transform: translateX(30%);
  }
  &__img4 {
    grid-column: 2 / span 3;
    grid-row: 24 / span 4;
    background-image: url("/src/assets/header.webp");
  }
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
  }
  & .discover {
    grid-column: 3 / span 2;
    grid-row: 11 / span 2;
  }
  & .culture__img2 {
    grid-column: 2 / span 4;
  }
  & .culture__img3 {
    grid-column: 1 / span 10;
    transform: translateX(-30%);
  }
  & .culture__img4 {
    grid-column: 9 / span 4;
  }
}
</style>
