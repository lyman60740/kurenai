<template>
  <section class="discover">
    <h2>
      <span style="text-align: center">Disover our menus and</span>
      <span style="text-align: left">indulge in an unforgettable</span>
      <span style="text-align: right">gastronomic experience,</span>
      <span style="text-align: left">combining culinary flavors</span>
      <span style="text-align: center">and refined cocktails.</span>
    </h2>
  </section>
</template>

<script>
export default {
  name: "Discover",
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
@use "/src/styles/variables";

.discover {
  display: flex;
  justify-content: center;
  align-items: center;
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
