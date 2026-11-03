<template>
  <header id="home" class="site-header">
    <!-- Top Header Bar -->
    <div class="top-header">
      <div class="container">
        <div class="d-flex align-items-center justify-content-between flex-wrap gap-3">
          <!-- Logo with simple yellow circle icon -->
          <a href="#home" class="brand-logo" @click.prevent="scrollToTop">
            <!-- Simple Yellow Circle Icon -->
            <div class="logo-circle"></div>
            <div>
              <h1 class="brand-title">Build<span class="logo-highlight">Icon</span></h1>
              <p class="brand-subtitle">CONSTRUCTION COMPANY</p>
            </div>
          </a>

          <!-- Right Header Cluster: Info Items aligned right next to Request a Quote Button -->
          <div class="header-right-cluster d-flex align-items-center ms-auto">
            <!-- Contact & Working Info (aligned together with quote button) -->
            <div class="header-info-items d-none d-md-flex align-items-center me-4">
              <!-- Custom Support & Sale -->
              <div class="header-info-item header-info-item-left">
                <i class="bi bi-phone header-info-icon"></i>
                <div>
                  <div class="header-info-label">Custom Support & Sale</div>
                  <div class="header-info-value">+7-495-1234567</div>
                </div>
              </div>

              <!-- Working Time -->
              <div class="header-info-item header-info-item-right">
                <i class="bi bi-clock header-info-icon"></i>
                <div>
                  <div class="header-info-label">Working Time</div>
                  <div class="header-info-value">MON–SAT: 08:00–18:00</div>
                </div>
              </div>
            </div>

            <!-- Request a Quote Button (Compact, aligned with contact info) -->
            <button class="btn-header-quote" @click="$emit('open-quote')">
              <i class="bi bi-envelope-fill"></i>
              REQUEST A QUOTE
            </button>
          </div>
        </div>
      </div>
    </div>

    <!-- Main Navigation Bar: Overlaps 50% on Header above and 50% on Hero under -->
    <div class="navbar-overlap-wrapper">
      <div class="container">
        <nav class="main-navbar">
          <!-- Mobile Menu Toggle Button -->
          <button 
            class="d-lg-none btn text-white p-2 border-0" 
            type="button" 
            @click="isMobileMenuOpen = !isMobileMenuOpen"
            aria-label="Toggle Navigation"
          >
            <i class="bi bi-list fs-3"></i>
          </button>

          <!-- Nav Links -->
          <div :class="['navbar-collapse-custom', { 'd-none d-lg-flex': !isMobileMenuOpen, 'd-flex flex-column flex-lg-row mobile-open': isMobileMenuOpen }]">
            <ul class="navbar-nav flex-lg-row align-items-stretch">
              <li class="nav-item">
                <a href="#home" class="nav-link-custom active" @click.prevent="scrollToTop">HOME</a>
              </li>
              <li class="nav-item">
                <a href="#about" class="nav-link-custom">ABOUT</a>
              </li>
              <li class="nav-item dropdown-item-custom">
                <a href="#services" class="nav-link-custom">
                  SERVICES
                  <i class="bi bi-chevron-down fs-8"></i>
                </a>
              </li>
              <li class="nav-item dropdown-item-custom">
                <a href="#projects" class="nav-link-custom">
                  PROJECTS
                  <i class="bi bi-chevron-down fs-8"></i>
                </a>
              </li>
              <li class="nav-item">
                <a href="#news" class="nav-link-custom">NEWS</a>
              </li>
              <li class="nav-item">
                <a href="#contact" class="nav-link-custom">CONTACT</a>
              </li>
            </ul>
          </div>

          <!-- Search Button -->
          <div class="ms-auto d-flex align-items-center pe-3">
            <button class="nav-search-btn" @click="$emit('toggle-search')" title="Search">
              <i class="bi bi-search"></i>
            </button>
          </div>
        </nav>
      </div>
    </div>
  </header>
</template>

<script setup>
import { ref } from 'vue'

defineEmits(['open-quote', 'toggle-search'])

const isMobileMenuOpen = ref(false)

const scrollToTop = () => {
  window.scrollTo({
    top: 0,
    behavior: 'smooth'
  })
  if (window.location.hash) {
    history.pushState(null, '', window.location.pathname)
  }
}
</script>

<style scoped>
.fs-8 {
  font-size: 10px;
}

@media (max-width: 991px) {
  .mobile-open {
    position: absolute;
    top: 100%;
    left: 0;
    right: 0;
    background-color: var(--primary-color);
    z-index: 100;
    padding: 10px 0;
    box-shadow: 0 8px 16px rgba(0,0,0,0.1);
  }
  .nav-link-custom {
    padding: 10px 16px !important;
  }
}
</style>
