<template>
  <div class="buildicon-app">
    <!-- Top Header & Yellow Navbar (Image 1) -->
    <TheHeader 
      @open-quote="isQuoteModalOpen = true"
      @toggle-search="isSearchModalOpen = true"
    />

    <!-- Main Hero Slider (Image 1) -->
    <HeroSlider />

    <!-- "We Are BuildWall" Callout Banner (Image 1 & 2) -->
    <CalloutBanner 
      @open-quote="isQuoteModalOpen = true"
    />

    <!-- 3 Feature Cards: Construction, About Us, Effective Teamwork (Image 2) -->
    <FeatureCards />

    <!-- Featured Projects 6-Grid Gallery with Filters (Image 3) -->
    <FeaturedProjects />

    <!-- Floating Scroll to Top Button (Image 2 & 3) -->
    <ScrollToTop />

    <!-- Interactive Quote Modal -->
    <QuoteModal 
      :is-open="isQuoteModalOpen" 
      @close="isQuoteModalOpen = false" 
    />

    <!-- Interactive Search Modal -->
    <SearchModal 
      :is-open="isSearchModalOpen" 
      @close="isSearchModalOpen = false" 
    />
  </div>
</template>

<script setup>
import { ref, onMounted } from 'vue'
import TheHeader from './components/TheHeader.vue'
import HeroSlider from './components/HeroSlider.vue'
import CalloutBanner from './components/CalloutBanner.vue'
import FeatureCards from './components/FeatureCards.vue'
import FeaturedProjects from './components/FeaturedProjects.vue'
import ScrollToTop from './components/ScrollToTop.vue'
import QuoteModal from './components/QuoteModal.vue'
import SearchModal from './components/SearchModal.vue'

const isQuoteModalOpen = ref(false)
const isSearchModalOpen = ref(false)

onMounted(() => {
  if (window.location.hash === '#home' || !window.location.hash) {
    window.scrollTo(0, 0)
    if (window.location.hash === '#home') {
      history.replaceState(null, '', window.location.pathname)
    }
  }
})
</script>

<style>
/* App wrapper */
.buildicon-app {
  min-height: 100vh;
  display: flex;
  flex-direction: column;
}
</style>
