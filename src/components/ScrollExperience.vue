<template>
  <section class="scroll-wrapper">
    <!-- Wrapper utama untuk pengalaman scroll -->
    <div class="panels">
      <!-- Loop setiap step/slide -->
      <div
        class="panel"
        v-for="(step, index) in steps"
        :key="index"
      >
        <div class="left">
          <!-- Judul navigasi kecil -->
          <p class="nav">
            plan <span>{{ step.highlight }}</span> build
          </p>

          <!-- Judul utama -->
          <h1 v-html="step.title"></h1>

          <!-- Deskripsi -->
          <p class="desc">
            {{ step.desc }}
          </p>

          <!-- Counter step -->
          <p class="count">{{ index + 1 }}/{{ steps.length }}</p>
        </div>

        <!-- Gambar / ilustrasi -->
        <div class="right">
          <img :src="step.image" alt="visual" />
        </div>
      </div>
    </div>
  </section>
</template>

<script>
// Import GSAP dan ScrollTrigger
import gsap from "gsap";
import ScrollTrigger from "gsap/ScrollTrigger";

// Daftarkan plugin ScrollTrigger
gsap.registerPlugin(ScrollTrigger);

export default {
  name: "ScrollExperience",

  data() {
    return {
      // Data untuk setiap step scroll
      steps: [
        {
          highlight: "design",
          title: "Peta situs<br />pengalaman tersebut",
          desc: "Lorem ipsum dolor sit amet, consectetur adipiscing elit.",
          image: require("@/assets/logo.png"),
        },
        {
          highlight: "build",
          title: "Saatnya mengecat<br />dinding kamar.",
          desc: "Lorem ipsum dolor sit amet, consectetur adipiscing elit.",
          image: require("@/assets/logo.png"),
        },
        {
          highlight: "launch",
          title: "Keajaiban terjadi<br />untuk membangunnya.",
          desc: "Lorem ipsum dolor sit amet, consectetur adipiscing elit.",
          image: require("@/assets/logo.png"),
        },
      ],
    };
  },

  mounted() {
    /**
     * Membuat animasi scroll berbasis GSAP ScrollTrigger
     * Section akan di-pin saat di-scroll
     * Setiap panel akan muncul berdasarkan posisi scroll
     */

    const panels = gsap.utils.toArray(".panel");

    // Timeline utama
    const tl = gsap.timeline({
      scrollTrigger: {
        trigger: ".scroll-wrapper", // Elemen pemicu scroll
        start: "top top",
        end: () => "+=" + window.innerHeight * panels.length,
        scrub: true, // Sinkron dengan scroll
        pin: true, // Section di-pin
      },
    });

    // Animasi tiap panel
    panels.forEach((panel, index) => {
      tl.fromTo(
        panel,
        { opacity: 0 },
        { opacity: 1, duration: 1 }
      );
    });
  },
};
</script>

<style lang="scss" scoped>
.scroll-wrapper {
  height: 100vh;
  overflow: hidden;
}

.panels {
  display: flex;
}

.panel {
  min-width: 100vw;
  height: 100vh;
  display: flex;
  align-items: center;
  justify-content: space-between;
}
</style>
