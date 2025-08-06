<script setup lang="ts">
import { Button } from '@/components/ui/button'
import { Card, CardContent, CardDescription, CardHeader, CardTitle } from '@/components/ui/card'
import { Input } from '@/components/ui/input'
import { Label } from '@/components/ui/label'
import { Alert, AlertDescription } from '@/components/ui/alert'
import { AlertTriangle } from 'lucide-vue-next'
</script>

<template>
  <div class="flex flex-col gap-6 max-w-md mx-auto">
    <Card>
      <CardHeader>
        <CardTitle>Login to your account</CardTitle>
        <CardDescription>Enter your credentials to access your account</CardDescription>
      </CardHeader>
      <CardContent>
        <form class="space-y-4">
          <div class="space-y-2">
            <Label for="username">Username</Label>
            <Input id="username" type="text" placeholder="Enter your username" required />
          </div>
          <div class="space-y-2">
            <Label for="password">Password</Label>
            <Input id="password" type="password" placeholder="Enter your password" required />
          </div>
          <!-- Error Alert at the bottom -->
          <Alert variant="destructive" class="mt-4">
            <AlertTriangle class="h-4 w-4" />
            <AlertDescription>
              Username or password incorrect. Please check your credentials and try again.
            </AlertDescription>
          </Alert>
          <Button type="submit" class="w-full"> Sign In </Button>
        </form>
      </CardContent>
    </Card>
  </div>
</template>
