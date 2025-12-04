<template>
  <a :href="project.link" target="_blank" class="card">
    <div v-if="project.image" class="thumb-wrap">
      <img :src="project.image" class="thumb" />
    </div>

    <h3 class="title">{{ project.title }}</h3>
    <p class="desc">{{ project.desc }}</p>
  </a>
</template>

<script setup>
const props = defineProps({
  project: {
    type: Object,
    required: true
  }
});
</script>

<style scoped>
.card {
  display: block;
  padding: 20px;
  border: 2px solid var(--stroke);
  border-radius: 10px;
  box-shadow: 3px 3px 0 var(--stroke);
  background: var(--bg);
  color: var(--text);
  text-decoration: none;
  transition: transform 0.2s ease, box-shadow 0.2s ease;
  max-width: 400px;
}

/* Sketch wobble hover effect */
.card:hover {
  transform: translate(-4px, -4px);
  box-shadow: 6px 6px 0 var(--stroke);
}

/* Thumbnail wrapper */
.thumb-wrap {
  width: 100%;
  height: 160px;
  border: 2px solid var(--stroke);
  border-radius: 8px;
  overflow: hidden;
  margin-bottom: 15px;
  box-shadow: 2px 2px 0 var(--stroke);
}

.thumb {
  width: 100%;
  height: 100%;
  object-fit: cover;
}

/* Title */
.title {
  font-family: "Kalam", cursive;
  font-size: 1.5rem;
  margin: 10px 0 8px;
  color: var(--text);
}

/* Description */
.desc {
  font-family: Inter, sans-serif;
  font-size: 1rem;
  opacity: 0.85;
  line-height: 1.5;
}
</style>
