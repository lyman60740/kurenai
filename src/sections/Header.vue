<template>
  <section class="header">
    <div class="header__content">
      <img src="/src/assets/logo_main.svg" alt="Logo" />
      <p>
        Step into Kurenai, where <br />
        elegance and Japanese <br />
        tradition converge in an <br />
        immersive
      </p>
    </div>
  </section>
</template>

<script>
import gsap from "gsap";
import jsonData from "../data/data.json";

export default {
  name: "Header",
  components: {},
  data() {
    return {};
  },
  mounted() {
    // Ici, vous pouvez utiliser GSAP pour des animations si nécessaire
  },
};
</script>

<style scoped lang="scss">
.header {
  width: 100%;
  height: 100svh;
  display: flex;
  justify-content: center;
  align-items: center;
  background-image: url("/src/assets/header.webp");
  background-size: cover;
  background-position: center;
  &__content {
    display: flex;
    flex-direction: column;
    gap: 81px;
    transform: translateY(30%);
    & p {
      font-size: 20px;
      font-weight: 300;
      text-transform: uppercase;
      color: #fff8e8;
      line-height: 30px;
      letter-spacing: 1px;
    }
  }
}
</style>
