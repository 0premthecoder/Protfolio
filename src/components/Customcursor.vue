<script setup>
import { ref, onMounted, computed } from 'vue'

const x = ref(0)
const y = ref(0)
const isPointer = ref(false)

const cursorStyle = computed(() => ({
  left: x.value + 'px',
  top: y.value + 'px',
  transform: isPointer.value ? "scale(1.4)" : "scale(1)"
}))

onMounted(() => {
  window.addEventListener('mousemove', e => {
    x.value = e.clientX + 5
    y.value = e.clientY + 5
    spawnPaintDot(e.clientX, e.clientY)
  })

  window.addEventListener('mouseover', e => {
    const tag = e.target
    if (tag.tagName === "A" || tag.tagName === "BUTTON") {
      isPointer.value = true
    } else {
      isPointer.value = false
    }
  })
})


function spawnPaintDot(xPos, yPos) {
  const dot = document.createElement('div')
  dot.className = 'paint-dot'
  dot.style.left = xPos + 'px'
  dot.style.top = yPos + 'px'

  document.getElementById('paint-layer').appendChild(dot)

  // Remove after 1 second
  setTimeout(() => {
    dot.remove()
  }, 1000)
}

</script>

<style scoped>
.cursor {
  position: fixed;
  transform: translate(-50%, -50%);
  pointer-events: none;
  font-size: 1.3rem;
  color: var(--text);
  opacity: 0.8;
  z-index: 10000;
  transition: transform 0.05s linear;
}
</style>
