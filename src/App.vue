<script setup lang="ts">
import LandingSection from './components/LandingSection.vue'
import MainForm from './components/MainForm.vue'

import { ref } from 'vue'

let isContentExpanded = ref(false)

const handleContentExpand = () => {
  isContentExpanded.value = !isContentExpanded.value
}
</script>

<template>
  <LandingSection :isContentExpanded="isContentExpanded" @expand-content="handleContentExpand" />
  <MainForm :isContentExpanded="isContentExpanded" />
</template>
