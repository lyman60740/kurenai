<template>
  <div class="jap-title">
    <div></div>
    <span>{{ text }}</span>
  </div>
</template>

<script>
export default {
  name: "JapTitle",
  props: {
    text: {
      type: String,
      required: true,
    },
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
