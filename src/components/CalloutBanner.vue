<template>
  <section class="callout-banner-section">
    <div class="container">
      <div class="d-flex align-items-center justify-content-between flex-wrap gap-4">
        <!-- Text Group -->
        <div class="d-flex align-items-center flex-wrap gap-4">
          <h2 class="callout-title">We Are BuildWall</h2>
          <p class="callout-text">
            We have been transforming the ideas and visions into award-winning projects.
          </p>
        </div>

        <!-- Button -->
        <div>
          <button class="btn-callout-quote" @click="$emit('open-quote')">
            <i class="bi bi-envelope-fill"></i>
            REQUEST A QUOTE
          </button>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup>
// Event om offerte popup te openen via bovenliggend component
defineEmits(['open-quote'])
</script>
