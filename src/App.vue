<template>
  <div id="app">
    <Navbar />
    <Customcursor/>
  <RoamingBug @bug-alert="triggerAlert"/>
   <SketchAlert 
    :show="showAlert"
    message="don't touch my pet pls 🛐"
    @close="showAlert = false"   
  />


  <div id="paint-layer"></div>
    <main class="page">
      <RouterView />
    </main>
  </div>
</template>

<script setup>
import Customcursor from './components/Customcursor.vue';
import Navbar from './components/Navbar.vue'
import RoamingBug from './components/RoamingBug.vue';
import SketchAlert from './components/SketchAlert.vue';
import { ref } from 'vue';


const showAlert = ref(false)

function triggerAlert() {
  showAlert.value = true
}

</script>

<style>
#app {
  background: var(--bg);
  color: var(--text);
}

.page {
  padding: 24px;
}
</style>
