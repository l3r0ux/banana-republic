<script setup lang="ts">
import LandingSection from './components/LandingSection.vue'
import MainForm from './components/MainForm.vue'

import { ref } from 'vue'

let isContentExpanded = ref(false)

const handleContentExpand = () => {
  isContentExpanded.value = !isContentExpanded.value

  if (isContentExpanded.value && window.innerWidth <= 960)
    window.scrollTo({
      behavior: 'smooth',
      top: window.innerHeight
    })
}
</script>

<template>
  <div class="main-content">
    <LandingSection
      class="landing-section"
      :isContentExpanded="isContentExpanded"
      @expand-content="handleContentExpand"
    />
    <MainForm class="main-form" :isContentExpanded="isContentExpanded" />
  </div>
</template>

<style scoped lang="scss">
@media screen and (min-width: 60rem) {
  .main-content {
    display: flex;

    .landing-section {
      flex: 3;
    }

    .main-form {
      flex: 5;
    }
  }
}
</style>
