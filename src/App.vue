<script setup lang="ts">
import { Button } from '@/components/ui/button'
import { SidebarProvider } from '@/components/ui/sidebar'
import AppSidebar from '@/components/AppSidebar.vue'
import { Toaster } from '@/components/ui/sonner'
import { toast } from 'vue-sonner'
import 'vue-sonner/style.css'

const handleClick = () => {
  toast.error('Event has been created', {
    description: 'Sunday, December 03, 2023 at 9:00 AM',
    duration: 3000,
    action: {
      label: 'Undo',
      onClick: () => console.log('Undo'),
    },
    cancel: {
      label: 'Cancel',
      onClick: () => console.log('Cancel'),
    },
  })
}
</script>

<template>
  <SidebarProvider>
    <AppSidebar />
    <main>
      <Button @click="handleClick">Click me</Button>
    </main>
  </SidebarProvider>
  <Toaster />
</template>
