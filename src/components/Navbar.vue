<template>
  <nav class="navbar">
    <div class="brand">Prem</div>

    <div class="links">
      <RouterLink to="/" class="link">Home</RouterLink>
      <RouterLink to="/projects" class="link">Projects</RouterLink>
      <RouterLink to="/about" class="link">About</RouterLink>
    </div>

    <button class="theme-toggle" @click="toggleTheme">
      <span v-if="theme === 'light'">🌙</span>
      <span v-else>☀️</span>
    </button>
  </nav>
</template>

<script setup>
import { ref, watch, onMounted } from 'vue'

const theme = ref(localStorage.getItem('theme') || 'light')

const toggleTheme = () => {
  theme.value = theme.value === 'light' ? 'dark' : 'light'
}

watch(theme, val => {
  document.documentElement.setAttribute('data-theme', val)
  localStorage.setItem('theme', val)
})

onMounted(() => {
  document.documentElement.setAttribute('data-theme', theme.value)
})
</script>

<style scoped>
.navbar {
  /* width: 100%; */
  padding: 14px 24px;
  display: flex;
  align-items: center;
  justify-content: space-between;

  border-bottom: 2px solid var(--stroke);
  background-color: var(--bg);
}

.brand {
  font-size: 1.5rem;
  font-weight: 600;
  font-family: 'Kalam', cursive;
  color: var(--text);
}

.links {
  display: flex;
  gap: 18px;
}

.link {
  position: relative;
  font-size: 1.05rem;
  color: var(--text);
  text-decoration: none;
  font-family: 'Inter', sans-serif;
}

.link::after {
  content: '';
  position: absolute;
  left: 0;
  bottom: -3px;
  width: 0%;
  height: 2px;
  background-color: var(--text);
  transition: width 0.25s ease;
  border-radius: 2px;
}

.link:hover::after {
  width: 100%;
}

.theme-toggle {
  background: transparent;
  border: 2px solid var(--stroke);
  border-radius: 6px;
  padding: 4px 8px;
  cursor: pointer;
  font-size: 1.1rem;
  color: var(--text);
}

/* Sketch-like aesthetic */
.navbar, .theme-toggle {
  box-shadow: 2px 2px 0 var(--stroke);
}
</style>
