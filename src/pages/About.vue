<template>
  <section class="about">

    <!-- Heading -->
    <h1 class="title">
      About Me
      <svg class="underline" viewBox="0 0 200 20">
        <path d="M5 15 Q 60 5 120 15 T 195 15" />
      </svg>
    </h1>

    <!-- Layout -->
    <div class="content">

      <!-- Sketch Avatar -->
      <div class="avatar-box">
        <div class="avatar">
          <!-- Replace later with your own sketch-image -->
            <img src="/src/assets/prem.png" alt="Prem" class="avatar-img" />

        </div>
      </div>

      <!-- Text -->
      <div class="text">
        <p>
          I'm Prem. A student, a builder, and someone who treats ideas 
          like living creatures that need to be sketched, challenged, and sharpened.
        </p>

        <p>
          I work at the intersection of DS, AI, design, and philosophy. 
          I enjoy turning messy thoughts into clean systems, 
          and creating things that feel both simple and intentional.
        </p>

        <p>
          Outside the technical world, I think a lot. 
          I enjoy philosophy, content creation, and exploring how people learn, grow, and build meaning.
        </p>

        <p>
          This portfolio is a reflection of that:  
          minimal, sketched, and honest.
        </p>
      </div>
    </div>

        <!-- Social Links -->
<div class="socials">
  <a 
    href="https://github.com/0premthecoder" 
    target="_blank" 
    class="social-link"
  >
    GitHub
  </a>

  <a 
    href="https://www.linkedin.com/in/prem-the-coder/" 
    target="_blank"
    class="social-link"
  >
    LinkedIn
  </a>

  <a 
    href="https://yt.oia.bio/mwv" 
    target="_blank"
    class="social-link"
    :hidden="true"
  >
    YouTube
  </a>
</div>

<!-- Tech Stack -->
<div class="tech-stack">
  <h2 class="tech-title">Tech Stack</h2>

  <div class="tech-list">
    <div class="tech-row">
      <span class="tech-dot"></span>
      <p>Vue.js / JavaScript / TypeScript</p>
    </div>

    <div class="tech-row">
      <span class="tech-dot"></span>
      <p>Python (Automation, Data Handling, Flask and Django)</p>
    </div>

    <div class="tech-row">
      <span class="tech-dot"></span>
      <p>HTML, CSS, Tailwind, UI/UX structuring</p>
    </div>

    <div class="tech-row">
      <span class="tech-dot"></span>
      <p>Node.js & APIs (basic backend)</p>
    </div>

    <div class="tech-row">
      <span class="tech-dot"></span>
      <p>DSA • AI/ML fundamentals (Building...)</p>
    </div>
  </div>
</div>


  </section>
</template>

<script setup>
// No JS required here for now
</script>

<style scoped>
/* Tech Stack Section */
.tech-stack {
  margin-top: 50px;
  padding-left: 15px;
  border-left: 3px dashed var(--stroke);
}

.tech-title {
  font-family: "Kalam", cursive;
  font-size: 2rem;
  margin-bottom: 20px;
  color: var(--text);
  position: relative;
}

/* Timeline List */
.tech-list {
  display: flex;
  flex-direction: column;
  gap: 20px;
}

/* Each row */
.tech-row {
  display: flex;
  align-items: center;
  gap: 14px;
  position: relative;
}

/* Dot (sketch style) */
.tech-dot {
  width: 12px;
  height: 12px;
  border: 2px solid var(--stroke);
  border-radius: 50%;
  background: var(--bg);
  box-shadow: 2px 2px 0 var(--stroke);
  flex-shrink: 0;
}

.tech-row p {
  margin: 0;
  font-size: 1rem;
  font-family: Inter, sans-serif;
  line-height: 1.5;
  color: var(--text);
}

/* Hover: wiggle the dot, like a sketch moment */
.tech-row:hover .tech-dot {
  transform: translate(-2px, -2px);
  box-shadow: 4px 4px 0 var(--stroke);
  transition: 0.15s ease;
}

/* Social section */
.socials {
  margin-top: 25px;
  display: flex;
  gap: 16px;
  flex-wrap: wrap;
}

.social-link {
  text-decoration: none;
  font-size: 1rem;
  font-family: Inter, sans-serif;
  color: var(--text);
  padding: 8px 14px;
  border: 2px solid var(--stroke);
  border-radius: 8px;
  box-shadow: 2px 2px 0 var(--stroke);
  transition: transform 0.15s ease, box-shadow 0.15s ease;
}

/* Sketch hover effect */
.social-link:hover {
  transform: translate(-2px, -2px);
  box-shadow: 4px 4px 0 var(--stroke);
}

.about {
  max-width: 900px;
  margin: 0 auto;
  padding: 60px 20px;
  animation: fadeIn 0.6s ease;
}

/* Title */
.title {
  font-family: "Kalam", cursive;
  font-size: 3rem;
  position: relative;
  display: inline-block;
  color: var(--text);
  margin-bottom: 40px;
}

.underline {
  width: 200px;
  height: 30px;
  position: absolute;
  bottom: -8px;
  left: 0;
}

.underline path {
  stroke: var(--stroke);
  stroke-width: 2.5;
  fill: none;
  stroke-dasharray: 300;
  stroke-dashoffset: 300;
  animation: draw 1.2s ease forwards;
}

/* Content Layout */
.content {
  display: flex;
  gap: 40px;
  flex-wrap: wrap;
  align-items: flex-start;
}

/* Avatar sketch box */
.avatar-box {
  flex: 1;
  min-width: 200px;
  max-width: 260px;
}

.avatar {
  width: 100%;
  aspect-ratio: 1 / 1;
  border: 2px solid var(--stroke);
  border-radius: 10px;
  box-shadow: 3px 3px 0 var(--stroke);
  background: var(--bg);
  display: flex;
  align-items: center;
  justify-content: center;
}

.avatar-sketch {
  font-size: 4rem;
  opacity: 0.7;
}
.avatar-img {
  width: 100%;
  height: 100%;
  object-fit: cover;
  filter: grayscale(90%);
  border-radius: 8px;

  /* subtle sketch effect */
  clip-path: polygon(
      2% 4%, 98% 0%, 100% 96%, 0% 100%
  );
  transition: filter 0.3s ease, transform 0.3s ease;
}

.avatar-img:hover {
  filter: grayscale(0%);
  transform: scale(1.02);
}

/* Text block */
.text {
  flex: 2;
  font-size: 1.15rem;
  line-height: 1.7;
  max-width: 600px;
}

.text p {
  margin-bottom: 18px;
}

/* Animations */
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
