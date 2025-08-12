<script setup lang="ts">
import { Button } from '@/components/ui/button'
import { SidebarProvider } from '@/components/ui/sidebar'
import AppSidebar from '@/components/AppSidebar.vue'
import { Toaster } from '@/components/ui/sonner'
import { toast } from 'vue-sonner'
import 'vue-sonner/style.css'

const handleClick = () => {
  document.documentElement.style.setProperty('--primary', 'oklch(0.577 0.245 27.325)')
}
</script>

<template>
  <SidebarProvider>
    <AppSidebar />
    <main>
      <Button @click="handleClick"> Click me </Button>
    </main>
  </SidebarProvider>
  <Toaster />
</template>
