<script setup lang="ts">
import { Button } from '@/components/ui/button'
import { Card, CardContent, CardDescription, CardHeader, CardTitle } from '@/components/ui/card'
import { Alert, AlertDescription } from '@/components/ui/alert'
import { CheckCircle } from 'lucide-vue-next'
</script>

<template>
  <div class="flex flex-col gap-6 max-w-md mx-auto">
    <Card>
      <CardHeader>
        <CardTitle>Account Settings</CardTitle>
        <CardDescription>Manage your account preferences and settings</CardDescription>
      </CardHeader>
      <CardContent class="space-y-4">
        <!-- Success Alert at the top -->
        <Alert variant="default">
          <CheckCircle class="h-4 w-4" />
          <AlertDescription>
            Your profile has been updated successfully! Changes are now active.
          </AlertDescription>
        </Alert>

        <div class="space-y-3">
          <div class="flex items-center justify-between p-3 border rounded-lg">
            <div>
              <h4 class="font-medium">Email Notifications</h4>
              <p class="text-sm text-muted-foreground">Receive updates via email</p>
            </div>
            <Button variant="outline" size="sm">Enabled</Button>
          </div>

          <div class="flex items-center justify-between p-3 border rounded-lg">
            <div>
              <h4 class="font-medium">Two-Factor Authentication</h4>
              <p class="text-sm text-muted-foreground">Enhanced security for your account</p>
            </div>
            <Button variant="outline" size="sm">Setup</Button>
          </div>

          <div class="flex items-center justify-between p-3 border rounded-lg">
            <div>
              <h4 class="font-medium">Theme Preference</h4>
              <p class="text-sm text-muted-foreground">Choose your display theme</p>
            </div>
            <Button variant="outline" size="sm">Dark</Button>
          </div>
        </div>

        <div class="pt-4">
          <Button class="w-full">Save Changes</Button>
        </div>
      </CardContent>
    </Card>
  </div>
</template>
