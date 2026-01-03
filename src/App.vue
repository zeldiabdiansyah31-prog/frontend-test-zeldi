<template>
  <div class="app">
    <HeroSection />
    <AboutSection />
    <ScrollExperience />
    <FeatureSection />
    <FooterSection />
  </div>
</template>

<script>
import HeroSection from "./components/HeroSection.vue";
import AboutSection from "./components/AboutSection.vue";
import ScrollExperience from "./components/ScrollExperience.vue";
import FeatureSection from "./components/FeatureSection.vue";
import FooterSection from "./components/FooterSection.vue";

export default {
  components: {
    HeroSection,
    AboutSection,
    ScrollExperience,
    FeatureSection,
    FooterSection
  }
};
</script>
