<script setup lang="ts">
import { Button } from '@/components/ui/button'
import { SidebarProvider } from '@/components/ui/sidebar'
import AppSidebar from '@/components/AppSidebar.vue'
import { Toaster } from '@/components/ui/sonner'
import 'vue-sonner/style.css'
import { useColorMode } from '@vueuse/core'

const mode = useColorMode({
  modes: {
    rose: 'rose',
    orange: 'orange',
  },
})
</script>

<template>
  <SidebarProvider>
    <AppSidebar />
    <main>
      <Button @click="mode = 'light'"> Light</Button>
      <Button @click="mode = 'dark'"> Dark</Button>
      <Button @click="mode = 'rose'"> Rose</Button>
      <Button @click="mode = 'orange'"> Orange</Button>
    </main>
  </SidebarProvider>
  <Toaster />
</template>
