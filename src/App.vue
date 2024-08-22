<template>
  <AppHeader />

  <main class="text-slate-900">
    <router-view />
  </main>
</template>

<script setup lang="ts">
import AppHeader from '@/components/AppHeader.vue'
</script>
