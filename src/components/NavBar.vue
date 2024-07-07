<template>
  <nav>
    <div class="lvl_nav">
      <div class="logo">
        <img src="/src/assets/logo.svg" alt="Logo" />
      </div>
      <ul class="nav-ancres">
        <li><a href="#">Bar</a></li>
        <li><a href="#">Kitchen</a></li>
        <li><a href="#">Event</a></li>
        <li><a href="#">Concept</a></li>
      </ul>
      <ul class="nav-infos">
        <li><a href="#">Menu</a></li>
        <li><a href="#">Book</a></li>
      </ul>
    </div>
  </nav>
</template>

<script setup></script>

<style scoped lang="scss">
nav {
  width: 100%;
  position: fixed;
  top: 0;
  left: 0;
  color: #fff8e8;
  font-family: "Manrope", sans-serif;
  text-transform: uppercase;
  padding: 0 40px;
  box-sizing: border-box;
  z-index: 19;
}
.lvl_nav {
  display: flex;
  justify-content: space-between;
  align-items: center;
  width: 100%;
  max-width: 1600px;
  margin: 0 auto;
  padding: 13px 0;
  box-sizing: border-box;
}
nav li {
  cursor: pointer;
}
.nav-ancres,
.nav-infos {
  display: flex;
  gap: 40px;
  font-size: 20px;
  font-weight: 300;
  padding: 20px 0;
}
</style>
