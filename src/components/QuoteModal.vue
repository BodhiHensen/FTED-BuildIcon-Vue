<template>
  <div v-if="isOpen" class="modal-backdrop-custom" @click.self="$emit('close')">
    <div class="modal-dialog-custom">
      <div class="modal-content-custom">
        <div class="modal-header-custom">
          <div>
            <h3 class="modal-title-custom">Request a Quote</h3>
            <p class="modal-subtitle-custom">Get a personalized project quotation</p>
          </div>
          <button class="btn-close-custom" @click="$emit('close')">
            <i class="bi bi-x-lg"></i>
          </button>
        </div>

        <form @submit.prevent="handleSubmit" class="modal-body-custom">
          <div v-if="submitted" class="alert alert-success">
            Thank you! Your quote request has been received. Our team will contact you shortly.
          </div>
          <div v-else>
            <div class="mb-3">
              <label class="form-label-custom">Your Name</label>
              <input v-model="form.name" type="text" class="form-control-custom" placeholder="Full name" required />
            </div>
            <div class="mb-3">
              <label class="form-label-custom">Email Address</label>
              <input v-model="form.email" type="email" class="form-control-custom" placeholder="name@example.com" required />
            </div>
            <div class="mb-3">
              <label class="form-label-custom">Phone Number</label>
              <input v-model="form.phone" type="tel" class="form-control-custom" placeholder="+1 (555) 000-0000" />
            </div>
            <div class="mb-3">
              <label class="form-label-custom">Service Needed</label>
              <select v-model="form.service" class="form-control-custom">
                <option value="construction">Construction & Building</option>
                <option value="renovation">House Renovation</option>
                <option value="interior">Interior Design</option>
                <option value="consulting">Construction Consultation</option>
              </select>
            </div>
            <div class="mb-4">
              <label class="form-label-custom">Project Description</label>
              <textarea v-model="form.message" class="form-control-custom" rows="3" placeholder="Tell us about your project..."></textarea>
            </div>
            <button type="submit" class="btn-submit-quote w-100">
              Submit Request
            </button>
          </div>
        </form>
      </div>
    </div>
  </div>
</template>

<script setup>
import { ref, reactive } from 'vue'

// Props van het bovenliggende component
defineProps({
  isOpen: Boolean
})

// Event om de popup te sluiten
const emit = defineEmits(['close'])

// Status of het formulier is verzonden
const submitted = ref(false)

// Reactieve formulierdata gekoppeld via v-model
const form = reactive({
  name: '',
  email: '',
  phone: '',
  service: 'construction',
  message: ''
})

// Formulier versturen
const handleSubmit = () => {
  submitted.value = true
  setTimeout(() => {
    submitted.value = false
    emit('close')
  }, 2000)
}
</script>

<style scoped>
.modal-backdrop-custom {
  position: fixed;
  top: 0;
  left: 0;
  width: 100vw;
  height: 100vh;
  background-color: rgba(34, 41, 49, 0.7);
  display: flex;
  align-items: center;
  justify-content: center;
  z-index: 1050;
  padding: 20px;
}

.modal-dialog-custom {
  max-width: 500px;
  width: 100%;
}

.modal-content-custom {
  background-color: #ffffff;
  box-shadow: 0 10px 40px rgba(0, 0, 0, 0.2);
  border-radius: 4px;
  overflow: hidden;
}

.modal-header-custom {
  background-color: var(--dark-color);
  color: #ffffff;
  padding: 22px 26px;
  display: flex;
  justify-content: space-between;
  align-items: flex-start;
}

.modal-title-custom {
  color: #ffffff;
  font-size: 20px;
  margin: 0;
  font-weight: 700;
}

.modal-subtitle-custom {
  color: #aeb6be;
  font-size: 13px;
  margin: 4px 0 0;
}

.btn-close-custom {
  background: transparent;
  border: none;
  color: #ffffff;
  font-size: 16px;
  cursor: pointer;
}

.modal-body-custom {
  padding: 26px;
}

.form-label-custom {
  font-size: 13px;
  font-weight: 600;
  color: var(--dark-heading);
  margin-bottom: 6px;
}

.form-control-custom {
  width: 100%;
  padding: 10px 14px;
  border: 1px solid #dcdfe3;
  border-radius: 2px;
  font-size: 14px;
  outline: none;
}

.form-control-custom:focus {
  border-color: var(--primary-color);
}

.btn-submit-quote {
  background-color: var(--primary-color);
  color: #ffffff;
  font-size: 13px;
  font-weight: 700;
  letter-spacing: 1px;
  text-transform: uppercase;
  padding: 14px;
  border: none;
  border-radius: 2px;
  cursor: pointer;
  transition: background-color 0.2s ease;
}

.btn-submit-quote:hover {
  background-color: var(--dark-color);
}
</style>
