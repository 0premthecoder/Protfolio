<template>
  <div class="bug" :class="{ frozen: isFrozen }" :style="styleObject">
    🐞
  </div>
</template>

<script setup>
import { ref, onMounted, computed } from 'vue'
const emit = defineEmits(["bug-alert"])

const x = ref(100)
const y = ref(100)
let dx = 1.2
let dy = 1.2

const cursorX = ref(0)
const cursorY = ref(0)

const isFrozen = ref(false)



const styleObject = computed(() => ({
  left: x.value + 'px',
  top: y.value + 'px'
}))

function animate() {
  const w = window.innerWidth
  const h = window.innerHeight

  // Distance between bug and cursor
  const dist = Math.hypot(cursorX.value - x.value, cursorY.value - y.value)

  // Freeze when cursor close
  if (dist < 120) {
    isFrozen.value = true
    emit("bug-alert")

  } else {
    isFrozen.value = false
    x.value += dx
    y.value += dy
  }

  // Bounce from edges
  if (x.value <= 0 || x.value >= w - 30) dx *= -1
  if (y.value <= 0 || y.value >= h - 30) dy *= -1

  // Slight random direction change
  if (Math.random() < 0.005) dx *= -1
  if (Math.random() < 0.005) dy *= -1

  requestAnimationFrame(animate)
}

onMounted(() => {
  window.addEventListener('mousemove', e => {
    cursorX.value = e.clientX
    cursorY.value = e.clientY
  })
  animate()

})
</script>

<style scoped>
.bug {
  position: fixed;
  font-size: 1.6rem;
  pointer-events: none;
  opacity: 0.75;
  z-index: 0;
  transition: transform 0.15s ease, filter 0.2s ease;
}

/* Freeze Style: squash + shaking */
.bug.frozen {
  animation: shake 0.3s infinite alternate ease-in-out;
  transform: scale(0.7) rotate(-8deg);
  filter: grayscale(70%);
}

/* Shake animation */
@keyframes shake {
  0% { transform: translate(1px, -1px) scale(0.7) rotate(-8deg); }
  100% { transform: translate(-1px, 1px) scale(0.7) rotate(-5deg); }
}
</style>
