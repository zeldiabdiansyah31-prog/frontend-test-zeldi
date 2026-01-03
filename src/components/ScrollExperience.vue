<template>
  <section class="scroll-wrapper">
    <div class="panels">
      <div
        class="panel"
        v-for="(step, index) in steps"
        :key="index"
      >
        <!-- LEFT CONTENT -->
        <div class="left">
          <p class="nav">
            plan <span>{{ step.highlight }}</span> build
          </p>

          <h1 v-html="step.title"></h1>

          <p class="desc">
            {{ step.desc }}
          </p>

          <p class="count">{{ index + 1 }}/3</p>
        </div>

        <!-- RIGHT IMAGE -->
        <div class="right">
          <img :src="step.image" alt="preview" />
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
          title: "The sitemap of<br/>the experience",
          desc: "Lorem ipsum dolor sit amet, consectetur adipiscing elit.",
          image: require("@/assets/logo.png")
        },
        {
          highlight: "design",
          title: "Time to paint<br/>the room walls",
          desc: "Lorem ipsum dolor sit amet, consectetur adipiscing elit.",
          image: require("@/assets/logo.png")
        },
        {
          highlight: "build",
          title: "Magic happens<br/>to build it out",
          desc: "Lorem ipsum dolor sit amet, consectetur adipiscing elit.",
          image: require("@/assets/logo.png")
        }
      ]
    };
  },
  mounted() {
    const panels = gsap.utils.toArray(".panel");

    gsap.to(panels, {
      xPercent: -100 * (panels.length - 1),
      ease: "none",
      scrollTrigger: {
        trigger: ".scroll-wrapper",
        pin: true,
        scrub: 1,
        snap: 1 / (panels.length - 1),
        end: "+=300%"
      }
    });
  }
};
</script>

<style lang="scss" scoped>
.scroll-wrapper {
  width: 100%;
  height: 100vh;
  overflow: hidden;
  background: #0b1205;
  color: #caff33;
}

.panels {
  display: flex;
  width: 300vw;
  height: 100%;
}

.panel {
  width: 100vw;
  display: grid;
  grid-template-columns: 1fr 1fr;
  align-items: center;
  padding: 0 80px;
}

.nav {
  font-size: 18px;

  span {
    text-decoration: underline;
  }
}

h1 {
  font-size: 48px;
  margin: 20px 0;
}

.desc {
  max-width: 420px;
}

.count {
  margin-top: 40px;
}

.right img {
  width: 100%;
  border-radius: 20px;
}

/* =========================
   RESPONSIVE
========================= */

@media (max-width: 1024px) {
  .panel {
    padding: 0 40px;
  }

  h1 {
    font-size: 40px;
  }
}

@media (max-width: 768px) {
  .panel {
    grid-template-columns: 1fr;
    text-align: center;
    padding: 40px 24px;
  }

  .left {
    order: 1;
  }

  .right {
    order: 2;
    margin-top: 24px;
  }

  h1 {
    font-size: 32px;
  }

  .desc {
    max-width: 100%;
    font-size: 14px;
  }

  .count {
    margin-top: 20px;
  }
}

@media (max-width: 480px) {
  h1 {
    font-size: 26px;
  }

  .nav {
    font-size: 14px;
  }
}
</style>
