<script setup lang="ts">
import LandingSection from './components/LandingSection.vue'
import MainForm from './components/MainForm.vue'

import { ref } from 'vue'

let isContentExpanded = ref(false)

const handleContentExpand = () => {
  isContentExpanded.value = !isContentExpanded.value

  if (isContentExpanded.value)
    window.scrollTo({
      behavior: 'smooth',
      top: window.innerHeight
    })
}
</script>

<template>
  <LandingSection :isContentExpanded="isContentExpanded" @expand-content="handleContentExpand" />
  <MainForm :isContentExpanded="isContentExpanded" />
</template>
