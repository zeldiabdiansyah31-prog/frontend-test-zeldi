<template>
  <div>
    <!-- HERO -->
    <HeroSection />

    <!-- ABOUT -->
    <AboutSection />

    <!-- SCROLL EXPERIENCE (SECTION UTAMA SESUAI SOAL) -->
    <ScrollExperience />

    <!-- FEATURE -->
    <FeatureSection />

    <!-- FOOTER -->
    <FooterSection />
  </div>
</template>

<script>
import HeroSection from "@/components/HeroSection.vue";
import AboutSection from "@/components/AboutSection.vue";
import FeatureSection from "@/components/FeatureSection.vue";
import FooterSection from "@/components/FooterSection.vue";
import ScrollExperience from "@/components/ScrollExperience.vue";

export default {
  name: "IndexPage",
  components: {
    HeroSection,
    AboutSection,
    ScrollExperience,
    FeatureSection,
    FooterSection
  }
};
</script>
