<script setup lang="ts">
import { SidebarProvider } from '@/components/ui/sidebar'
import AppSidebar from '@/components/AppSidebar.vue'
</script>

<template>
  <SidebarProvider>
    <AppSidebar />
    <main>hello world</main>
  </SidebarProvider>
</template>
