<template>
  <div class="alert" v-if="visible">
    {{ message }}
  </div>
</template>

<script setup>
import { ref, watch } from 'vue'

const props = defineProps({
  show: Boolean,
  message: {
    type: String,
    default: "Alert"
  }
})

const emit = defineEmits(["close"]) // tell parent when done

const visible = ref(false)

// When parent sets show = true, we open → wait → auto close
watch(() => props.show, newVal => {
  if (newVal) {
    visible.value = true

    setTimeout(() => {
      visible.value = false
      emit("close") 
    }, 2000) // auto hide after 2 seconds
  }
})
</script>

<style scoped>
.alert {
  position: fixed;
  bottom: 40px;
  left: 50%;
  transform: translateX(-50%);
  background: var(--bg);
  color: var(--text);
  padding: 12px 20px;
  border: 2px solid var(--stroke);
  border-radius: 10px;
  box-shadow: 3px 3px 0 var(--stroke);
  font-family: Inter, sans-serif;
  z-index: 9999;
  animation: popIn 0.3s ease-out;
}

@keyframes popIn {
  from {
    opacity: 0;
    transform: translateX(-50%) translateY(8px) scale(0.95);
  }
  to {
    opacity: 1;
    transform: translateX(-50%) translateY(0) scale(1);
  }
}
</style>
