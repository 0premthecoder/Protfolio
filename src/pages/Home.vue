<template>
  <section class="home">

    <!-- Hero Section -->
    <div class="hero">
      <h1 class="hero-title">
        Prem
        <svg class="underline" viewBox="0 0 200 20">
          <path d="M5 10 Q 60 20 120 10 T 195 10" />
        </svg>
      </h1>

      <p class="subtitle">developer • thinker • builder</p>
    </div>

    <!-- Intro Block -->
    <div class="intro-block">
      <p>
        I build tools, think loudly, and sketch ideas into the world.
        Currently working with DS, AI, design, and philosophy-driven content.
      </p>
    </div>

    <!-- CTA Buttons -->
    <div class="buttons">
      <RouterLink to="/projects" class="btn">View Projects</RouterLink>
      <RouterLink to="/about" class="btn">About Me</RouterLink>
    </div>

    <!-- Little sketch doodles -->
    <div class="doodle star">✦</div>
    <div class="doodle arrow">➜</div>

  </section>
</template>

<script setup>
// No scripts needed yet. Pure view.
</script>

<style scoped>
.home {
  max-width: 850px;
  margin: 0 auto;
  padding: 60px 20px;
  position: relative;
  animation: fadeIn 0.8s ease;
}

/* HERO */
.hero-title {
  font-family: "Kalam", cursive;
  font-size: 4rem;
  margin: 0;
  position: relative;
  display: inline-block;
  color: var(--text);
}

.subtitle {
  font-family: Inter, sans-serif;
  font-size: 1.2rem;
  margin-top: 10px;
  opacity: 0.8;
}

/* Underline sketch */
.underline {
  width: 200px;
  height: 30px;
  position: absolute;
  bottom: -10px;
  left: 0;
}

.underline path {
  stroke: var(--stroke);
  stroke-width: 2.5;
  fill: none;
  stroke-linecap: round;
  stroke-dasharray: 300;
  stroke-dashoffset: 300;
  animation: draw 1.2s ease forwards;
}

/* INTRO BLOCK */
.intro-block {
  margin-top: 40px;
  padding: 18px 20px;
  border: 2px solid var(--stroke);
  border-radius: 8px;
  box-shadow: 2px 2px 0 var(--stroke);
  font-size: 1.1rem;
  line-height: 1.6;
  background: var(--bg);
  max-width: 650px;
}

/* BUTTONS */
.buttons {
  margin-top: 40px;
  display: flex;
  gap: 20px;
}

.btn {
  padding: 10px 20px;
  border: 2px solid var(--stroke);
  border-radius: 6px;
  text-decoration: none;
  color: var(--text);
  font-size: 1rem;
  font-family: Inter, sans-serif;
  box-shadow: 2px 2px 0 var(--stroke);
  transition: transform 0.15s ease;
  position: relative;
}

.btn:hover {
  transform: translate(-2px, -2px);
  box-shadow: 4px 4px 0 var(--stroke);
}

/* DOODLES */
.doodle {
  font-size: 2rem;
  opacity: 0.5;
  position: absolute;
  color: var(--text);
  pointer-events: none;
}

.star {
  top: 45px;
  right: 30px;
}

.arrow {
  bottom: 40px;
  left: 20px;
  transform: rotate(10deg);
}

/* ANIMATIONS */
@keyframes draw {
  to {
    stroke-dashoffset: 0;
  }
}

@keyframes fadeIn {
  from {
    opacity: 0;
    transform: translateY(12px);
  }
  to {
    opacity: 1;
    transform: translateY(0);
  }
}
</style>
