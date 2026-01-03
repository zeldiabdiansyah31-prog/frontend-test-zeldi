<template>
  <section class="feature-section">
    <h2>Fitur Unggulan</h2>

    <!-- INI TEMPAT <ul> -->
    <ul>
      <li class="feature-item">Vue.js 2</li>
      <li class="feature-item">SASS</li>
      <li class="feature-item">GSAP Scroll</li>
    </ul>
  </section>
</template>

<script>
import gsap from "gsap";
import ScrollTrigger from "gsap/ScrollTrigger";

gsap.registerPlugin(ScrollTrigger);

export default {
  name: "FeatureSection",
  mounted() {
    gsap.from(".feature-item", {
      scrollTrigger: {
        trigger: ".feature-section",
        start: "top 80%",
      },
      opacity: 0,
      y: 60,
      stagger: 0.2,
      duration: 0.8
    });
  }
};
</script>

<style lang="scss" scoped>
.feature-section {
  padding: 100px 20px;
  text-align: center;
  background: #f1f5f9;

  ul {
    list-style: none;
    padding: 0;
  }

  .feature-item {
    font-size: 20px;
    margin: 16px 0;
  }
}
</style>
