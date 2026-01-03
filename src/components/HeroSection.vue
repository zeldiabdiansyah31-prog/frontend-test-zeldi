<template>
  <section class="hero-section">
    <h1 class="hero-title">Landing Page Test</h1>
    <p>Vue.js 2 + SASS</p>
  </section>
</template>

<script>
import gsap from "gsap";

export default {
  name: "HeroSection",

  mounted() {
    gsap.from(".hero-title", {
      opacity: 0,
      y: 80,
      duration: 1
    });
  }
};
</script>

<style lang="scss" scoped>
.hero-section {
  min-height: 100vh;
  background: #0f172a;
  color: white;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
}

.hero-title {
  font-size: 48px;
}
</style>
