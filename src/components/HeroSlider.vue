<template>
  <section class="hero-slider-container">
    <!-- Prev Arrow Button -->
    <button 
      class="hero-nav-arrow hero-nav-prev" 
      @click="prevSlide" 
      aria-label="Previous Slide"
    >
      <i class="bi bi-chevron-left"></i>
    </button>

    <!-- Next Arrow Button -->
    <button 
      class="hero-nav-arrow hero-nav-next" 
      @click="nextSlide" 
      aria-label="Next Slide"
    >
      <i class="bi bi-chevron-right"></i>
    </button>

    <!-- Slides -->
    <div 
      v-for="(slide, index) in slides" 
      :key="index"
      :class="['hero-slide', { 'active': currentSlide === index }]"
      :style="{ backgroundImage: `url(${slide.image})` }"
    >
      <div class="container position-relative">
        <div class="hero-content">
          <!-- Yellow Dash -->
          <div class="hero-dash"></div>

          <!-- Subtitle -->
          <div class="hero-subtitle">{{ slide.subtitle }}</div>

          <!-- Main Heading -->
          <h2 class="hero-title" v-html="slide.title"></h2>

          <!-- Action Buttons -->
          <div class="hero-buttons">
            <a href="#services" class="btn-hero-primary">
              {{ slide.btnPrimaryText }}
              <i class="bi bi-chevron-right fs-9"></i>
            </a>
            <a href="#about" class="btn-hero-dark">
              {{ slide.btnSecondaryText }}
              <i class="bi bi-chevron-right fs-9"></i>
            </a>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup>
import { ref } from 'vue'

const currentSlide = ref(0)

const slides = [
  {
    image: '/images/hero1.jpg',
    subtitle: 'HIGH QUALITY GARANTIED',
    title: 'Constructing<br>Is Our Life Business',
    btnPrimaryText: 'OUR SERVICES',
    btnSecondaryText: 'ABOUT US'
  },
  {
    image: '/images/hero2.jpg',
    subtitle: 'HIGH QUALITY GARANTIED',
    title: "We're Ready To Bring<br>The Mostcomplex Projects to Life",
    btnPrimaryText: 'OUR SERVICES',
    btnSecondaryText: 'ABOUT US'
  },
  {
    image: '/images/hero3.jpg',
    subtitle: 'COMMITTED TO BUILDING',
    title: 'Building The Future<br>With Passion and Precision',
    btnPrimaryText: 'OUR SERVICES',
    btnSecondaryText: 'ABOUT US'
  }
]

const nextSlide = () => {
  currentSlide.value = (currentSlide.value + 1) % slides.length
}

const prevSlide = () => {
  currentSlide.value = (currentSlide.value - 1 + slides.length) % slides.length
}
</script>

<style scoped>
.fs-9 {
  font-size: 11px;
}
</style>
