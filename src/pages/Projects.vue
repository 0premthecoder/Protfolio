<template>
  <div class="projects-page">
    <header class="header">
      <h2>Projects</h2>
      <p class="tagline">
        A selected set of things I’ve actually finished, not just thought about.
      </p>
    </header>

    <div class="grid">
      <ProjectCard
        v-for="(p, i) in projectList"
        :key="i"
        :project="p"
      />
    </div>
  </div>
</template>

<script setup>
import { projects } from "../data/projects";
import ProjectCard from "../components/ProjectCard.vue";

const projectList = projects;
</script>

<style scoped>
.projects-page {
  padding: 80px 40px 60px;
  max-width: 1120px;
  margin: 0 auto;
}

.header h2 {
  font-size: 2.1rem;
  font-family: "Courier New", monospace;
  text-transform: uppercase;
  letter-spacing: 0.16em;
  margin-bottom: 8px;
}

.tagline {
  color: var(--muted);
  font-size: 0.98rem;
}

.grid {
  margin-top: 36px;
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(280px, 1fr));
  gap: 26px;
}

@media (max-width: 768px) {
  .projects-page {
    padding: 70px 20px 40px;
  }
}
</style>
