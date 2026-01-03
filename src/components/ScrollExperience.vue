<template>
  <section class="scroll-wrapper">
    <div class="panels">
      <div
        class="panel"
        v-for="(step, index) in steps"
        :key="index"
      >
        <div class="left">
          <p class="nav">
            plan <span>{{ step.highlight }}</span> build
          </p>

          <h1 class="title">{{ step.title }}</h1>

          <p class="desc">
            {{ step.desc }}
          </p>

          <p class="count">{{ index + 1 }}/{{ steps.length }}</p>
        </div>

        <div class="right">
          <img :src="step.image" />
        </div>
      </div>
    </div>
  </section>
</template>

<script>
import gsap from "gsap";
import ScrollTrigger from "gsap/ScrollTrigger";

gsap.registerPlugin(ScrollTrigger);

export default {
  name: "ScrollExperience",
  data() {
    return {
      steps: [
        {
          highlight: "design",
          title: "Peta situs pengalaman tersebut",
          desc: "Lorem ipsum dolor sit amet, consectetur adipiscing elit.",
          image: require("@/assets/logo.png"),
        },
        {
          highlight: "build",
          title: "Saatnya mengecat dinding kamar.",
          desc: "Lorem ipsum dolor sit amet, consectetur adipiscing elit.",
          image: require("@/assets/logo.png"),
        },
        {
          highlight: "launch",
          title: "Keajaiban terjadi untuk membangunnya.",
          desc: "Lorem ipsum dolor sit amet, consectetur adipiscing elit.",
          image: require("@/assets/logo.png"),
        },
      ],
    };
  },
  mounted() {
    const panels = gsap.utils.toArray(".panel");

    // 🔹 Horizontal scroll + SNAP (INI KUNCI 90%)
    gsap.to(panels, {
      xPercent: -100 * (panels.length - 1),
      ease: "none",
      scrollTrigger: {
        trigger: ".scroll-wrapper",
        pin: true,
        scrub: 1,
        snap: 1 / (panels.length - 1), // ⬅️ SNAP PER PANEL
        end: () => "+=" + window.innerWidth * panels.length,
      },
    });

    // 🔹 Animasi teks masuk tiap panel
    panels.forEach((panel) => {
      gsap.from(panel.querySelectorAll(".nav, .title, .desc, .count"), {
        opacity: 0,
        y: 40,
        stagger: 0.15,
        duration: 0.8,
        ease: "power3.out",
        scrollTrigger: {
          trigger: panel,
          start: "left center",
          toggleActions: "play none none reverse",
        },
      });
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
  height: 100%;
}

.panel {
  min-width: 100vw;
  height: 100vh;
  display: flex;
  align-items: center;
  padding: 0 8vw;
  background: #0a0f0a;
  color: #d7ff3f;

  .left {
    flex: 1;
  }

  .right {
    flex: 1;
    display: flex;
    justify-content: center;

    img {
      width: 70%;
      max-width: 400px;
    }
  }

  .nav {
    font-size: 14px;
    text-transform: uppercase;

    span {
      color: #9cff00;
    }
  }

  .title {
    font-size: 48px;
    margin: 16px 0;
  }

  .desc {
    max-width: 420px;
  }

  .count {
    margin-top: 40px;
    font-size: 14px;
  }
}

/* 🔹 MOBILE STACKING (BONUS NILAI) */
@media (max-width: 768px) {
  .panel {
    flex-direction: column;
    text-align: center;

    .right {
      margin-top: 24px;

      img {
        width: 50%;
      }
    }
  }
}
</style>
