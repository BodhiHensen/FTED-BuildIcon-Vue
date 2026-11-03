<template>
  <div v-if="isOpen" class="search-backdrop-custom" @click.self="$emit('close')">
    <div class="search-box-custom">
      <div class="d-flex align-items-center gap-3">
        <i class="bi bi-search fs-4 text-warning"></i>
        <input 
          v-model="query" 
          type="text" 
          class="search-input-custom" 
          placeholder="Search site..." 
          autofocus
          @keyup.enter="handleSearch"
        />
        <button class="btn text-white fs-4" @click="$emit('close')">
          <i class="bi bi-x-lg"></i>
        </button>
      </div>
    </div>
  </div>
</template>

<script setup>
import { ref } from 'vue'

// Props en events voor het openen en sluiten van de zoekbalk
defineProps({
  isOpen: Boolean
})
const emit = defineEmits(['close'])

// Ingevulde zoekterm gekoppeld via v-model
const query = ref('')

// Zoekopdracht uitvoeren bij enter
const handleSearch = () => {
  if (query.value.trim()) {
    alert(`Searching for: ${query.value}`)
    emit('close')
  }
}
</script>

<style scoped>
.search-backdrop-custom {
  position: fixed;
  top: 0;
  left: 0;
  width: 100vw;
  height: 100vh;
  background-color: rgba(34, 41, 49, 0.95);
  display: flex;
  align-items: center;
  justify-content: center;
  z-index: 1100;
  padding: 20px;
}

.search-box-custom {
  max-width: 650px;
  width: 100%;
  border-bottom: 2px solid var(--primary-color);
  padding-bottom: 12px;
}

.search-input-custom {
  width: 100%;
  background: transparent;
  border: none;
  font-size: 26px;
  color: #ffffff;
  outline: none;
  font-family: var(--font-heading);
}

.search-input-custom::placeholder {
  color: rgba(255, 255, 255, 0.4);
}
</style>
