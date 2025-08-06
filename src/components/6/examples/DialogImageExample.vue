<script setup lang="ts">
import { Button } from '@/components/ui/button'
import {
  Dialog,
  DialogContent,
  DialogHeader,
  DialogTitle,
  DialogDescription,
  DialogTrigger,
} from '@/components/ui/dialog'
import { Card, CardContent } from '@/components/ui/card'
import { ImageIcon, ZoomIn } from 'lucide-vue-next'
</script>

<template>
  <div class="flex flex-col gap-6 max-w-4xl mx-auto mt-10">
    <div class="text-center space-y-2">
      <h2 class="text-2xl font-bold">Image Gallery</h2>
      <p class="text-muted-foreground">Click on any image to view it in full size</p>
    </div>

    <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-4">
      <!-- Image 1 -->
      <Dialog>
        <DialogTrigger as-child>
          <Card class="cursor-pointer hover:shadow-lg transition-shadow group">
            <CardContent class="p-4">
              <div
                class="relative aspect-square bg-gradient-to-br from-blue-100 to-blue-200 rounded-lg flex items-center justify-center overflow-hidden"
              >
                <ImageIcon class="w-16 h-16 text-blue-500" />
                <div
                  class="absolute inset-0 bg-black/0 group-hover:bg-black/10 transition-colors flex items-center justify-center"
                >
                  <ZoomIn
                    class="w-8 h-8 text-white opacity-0 group-hover:opacity-100 transition-opacity"
                  />
                </div>
                <div
                  class="absolute bottom-2 left-2 bg-black/70 text-white text-xs px-2 py-1 rounded"
                >
                  Nature Landscape
                </div>
              </div>
            </CardContent>
          </Card>
        </DialogTrigger>
        <DialogContent class="max-w-4xl">
          <DialogHeader>
            <DialogTitle>Nature Landscape</DialogTitle>
          </DialogHeader>
          <div class="space-y-4">
            <div
              class="aspect-video bg-gradient-to-br from-blue-100 to-blue-200 rounded-lg flex items-center justify-center"
            >
              <ImageIcon class="w-24 h-24 text-blue-500" />
            </div>
            <div class="space-y-2">
              <p class="text-sm text-muted-foreground">
                <strong>Description:</strong>
                <DialogDescription as-child>
                  <span>
                    A beautiful landscape showcasing nature's beauty with rolling hills and clear
                    skies.
                  </span>
                </DialogDescription>
              </p>
              <p class="text-sm text-muted-foreground">
                <strong>Dimensions:</strong> 1920 x 1080 px
              </p>
              <p class="text-sm text-muted-foreground"><strong>Date:</strong> December 15, 2024</p>
            </div>
          </div>
        </DialogContent>
      </Dialog>

      <!-- Image 2 -->
      <Dialog>
        <DialogTrigger as-child>
          <Card class="cursor-pointer hover:shadow-lg transition-shadow group">
            <CardContent class="p-4">
              <div
                class="relative aspect-square bg-gradient-to-br from-purple-100 to-purple-200 rounded-lg flex items-center justify-center overflow-hidden"
              >
                <ImageIcon class="w-16 h-16 text-purple-500" />
                <div
                  class="absolute inset-0 bg-black/0 group-hover:bg-black/10 transition-colors flex items-center justify-center"
                >
                  <ZoomIn
                    class="w-8 h-8 text-white opacity-0 group-hover:opacity-100 transition-opacity"
                  />
                </div>
                <div
                  class="absolute bottom-2 left-2 bg-black/70 text-white text-xs px-2 py-1 rounded"
                >
                  City Architecture
                </div>
              </div>
            </CardContent>
          </Card>
        </DialogTrigger>
        <DialogContent class="max-w-4xl">
          <DialogHeader>
            <DialogTitle>City Architecture</DialogTitle>
          </DialogHeader>
          <div class="space-y-4">
            <div
              class="aspect-video bg-gradient-to-br from-purple-100 to-purple-200 rounded-lg flex items-center justify-center"
            >
              <ImageIcon class="w-24 h-24 text-purple-500" />
            </div>
            <div class="space-y-2">
              <p class="text-sm text-muted-foreground">
                <strong>Description:</strong>
                <DialogDescription as-child>
                  <span>
                    Modern architectural design featuring innovative building structures and urban
                    planning.
                  </span>
                </DialogDescription>
              </p>
              <p class="text-sm text-muted-foreground">
                <strong>Dimensions:</strong> 1920 x 1080 px
              </p>
              <p class="text-sm text-muted-foreground"><strong>Date:</strong> December 10, 2024</p>
            </div>
          </div>
        </DialogContent>
      </Dialog>

      <!-- Image 3 -->
      <Dialog>
        <DialogTrigger as-child>
          <Card class="cursor-pointer hover:shadow-lg transition-shadow group">
            <CardContent class="p-4">
              <div
                class="relative aspect-square bg-gradient-to-br from-green-100 to-green-200 rounded-lg flex items-center justify-center overflow-hidden"
              >
                <ImageIcon class="w-16 h-16 text-green-500" />
                <div
                  class="absolute inset-0 bg-black/0 group-hover:bg-black/10 transition-colors flex items-center justify-center"
                >
                  <ZoomIn
                    class="w-8 h-8 text-white opacity-0 group-hover:opacity-100 transition-opacity"
                  />
                </div>
                <div
                  class="absolute bottom-2 left-2 bg-black/70 text-white text-xs px-2 py-1 rounded"
                >
                  Abstract Art
                </div>
              </div>
            </CardContent>
          </Card>
        </DialogTrigger>
        <DialogContent class="max-w-4xl">
          <DialogHeader>
            <DialogTitle>Abstract Art</DialogTitle>
          </DialogHeader>
          <div class="space-y-4">
            <div
              class="aspect-video bg-gradient-to-br from-green-100 to-green-200 rounded-lg flex items-center justify-center"
            >
              <ImageIcon class="w-24 h-24 text-green-500" />
            </div>
            <div class="space-y-2">
              <p class="text-sm text-muted-foreground">
                <strong>Description:</strong>
                <DialogDescription as-child>
                  <span>
                    Creative abstract composition with vibrant colors and flowing geometric
                    patterns.
                  </span>
                </DialogDescription>
              </p>
              <p class="text-sm text-muted-foreground">
                <strong>Dimensions:</strong> 1920 x 1080 px
              </p>
              <p class="text-sm text-muted-foreground"><strong>Date:</strong> December 8, 2024</p>
            </div>
          </div>
        </DialogContent>
      </Dialog>
    </div>

    <div class="text-center">
      <Button variant="outline"> Load More Images </Button>
    </div>
  </div>
</template>
