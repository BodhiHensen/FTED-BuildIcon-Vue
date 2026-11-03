<template>
  <Transition name="fade">
    <button 
      v-show="isVisible"
      class="scroll-to-top-btn" 
      @click="scrollToTop" 
      title="Scroll to Top"
    >
      <i class="bi bi-arrow-up-short fs-6"></i>
      TOP
    </button>
  </Transition>
</template>

<script setup>
import { ref, onMounted, onUnmounted } from 'vue'

// Zichtbaarheid van de scroll-naar-boven knop
const isVisible = ref(false)

// Toon de knop als de gebruiker meer dan 200px naar beneden scrollt
const handleScroll = () => {
  isVisible.value = window.scrollY > 200
}

// Soepel naar boven scrollen bij klik
const scrollToTop = () => {
  window.scrollTo({
    top: 0,
    behavior: 'smooth'
  })
}

// Event listeners toevoegen en opruimen
onMounted(() => {
  window.addEventListener('scroll', handleScroll, { passive: true })
  handleScroll()
})

onUnmounted(() => {
  window.removeEventListener('scroll', handleScroll)
})
</script>

<style scoped>
.fade-enter-active,
.fade-leave-active {
  transition: opacity 0.3s ease, transform 0.3s ease;
}

.fade-enter-from,
.fade-leave-to {
  opacity: 0;
  transform: translateY(10px);
}
</style>
