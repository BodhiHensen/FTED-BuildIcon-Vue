<template>
  <section id="projects" class="featured-projects-section">
    <div class="container">
      <!-- Section Title -->
      <h2 class="projects-header-title">FEATURED PROJECTS</h2>

      <!-- Category Filter Tabs -->
      <div class="projects-filter-nav">
        <button 
          v-for="cat in categories" 
          :key="cat.id"
          :class="['filter-btn', { 'active': activeCategory === cat.id }]"
          @click="setCategory(cat.id)"
        >
          {{ cat.name }}
        </button>
      </div>
    </div>

    <!-- 6-Grid Projects (3 columns, 2 rows) -->
    <div class="projects-grid">
      <div 
        v-for="project in filteredProjects" 
        :key="project.id"
        :class="['project-tile', { 'always-active': activeProjectId === project.id }]"
        @mouseenter="hoverProject(project.id)"
        @mouseleave="unhoverProject"
      >
        <!-- Background Image -->
        <img 
          :src="project.image" 
          :alt="project.title" 
          class="project-tile-img"
        />

        <!-- Translucent Dark Overlay -->
        <div class="project-tile-overlay">
          <h3 class="project-overlay-title">{{ project.title }}</h3>
          <p class="project-overlay-desc">{{ project.description }}</p>
          <a :href="project.link || '#'" class="project-overlay-link">
            LEARN MORE
            <i class="bi bi-chevron-right fs-9"></i>
          </a>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup>
import { ref, computed } from 'vue'

// Actieve filtercategorie en geselecteerd project
const activeCategory = ref('all')
const activeProjectId = ref(2)
const hoveredProjectId = ref(null)

// Beschikbare categorieën voor de tabs
const categories = [
  { id: 'all', name: 'ALL' },
  { id: 'building', name: 'BUILDING' },
  { id: 'consulting', name: 'CONSULTING' },
  { id: 'interior', name: 'INTERIOR' },
  { id: 'office', name: 'OFFICE' }
]

const allProjects = [
  {
    id: 1,
    title: 'Limoges, France',
    description: 'Buildwall has worked on this site continuously since 2006 and enjoys a long-standing relationship with Shell Canada. In June 2010,...',
    image: '/images/proj1.jpg',
    categories: ['all', 'building', 'consulting'],
    link: '#projects'
  },
  {
    id: 2,
    title: 'Shreveport, Bossier City',
    description: 'This luxury resort and senior independent living facility with a fitness center, pool, spa, sauna, hair salon, classroom space and...',
    image: '/images/proj2.jpg',
    categories: ['all', 'building', 'interior'],
    link: '#projects'
  },
  {
    id: 3,
    title: 'The Nines, NY',
    description: 'In June 2010, Buildwall completed crushing and conveying offsite work. Shell Canada. In June 2010 has worked on this site...',
    image: '/images/proj3.jpg',
    categories: ['all', 'building', 'office'],
    link: '#projects'
  },
  {
    id: 4,
    title: 'Twelve West, Portland',
    description: 'Buildwall has worked on this site continuously since 2006 and enjoys a long-standing relationship with Shell Canada. In June 2010,...',
    image: '/images/proj4.jpg',
    categories: ['all', 'consulting', 'office'],
    link: '#projects'
  },
  {
    id: 5,
    title: 'Palm Bay, Florida',
    description: 'This luxury resort and senior independent living facility with a fitness center, pool, spa, sauna, hair salon, classroom space and...',
    image: '/images/proj5.jpg',
    categories: ['all', 'interior'],
    link: '#projects'
  },
  {
    id: 6,
    title: 'Clean Water, Memphis',
    description: 'In June 2010, Buildwall completed crushing and conveying offsite work. Shell Canada. In June 2010 has worked on this site...',
    image: '/images/proj6.jpg',
    categories: ['all', 'building', 'consulting'],
    link: '#projects'
  }
]

// Filter de projecten automatisch op basis van de gekozen categorie
const filteredProjects = computed(() => {
  if (activeCategory.value === 'all') {
    return allProjects
  }
  return allProjects.filter(p => p.categories.includes(activeCategory.value))
})

// Categorie aanpassen bij tab klik
const setCategory = (catId) => {
  activeCategory.value = catId
}

const hoverProject = (id) => {
  hoveredProjectId.value = id
  activeProjectId.value = id
}

const unhoverProject = () => {
  hoveredProjectId.value = null
  // Keep Shreveport Bossier City active when not hovering any other tile, matching Image 3
  activeProjectId.value = 2
}
</script>

<style scoped>
.fs-9 {
  font-size: 11px;
}
</style>
