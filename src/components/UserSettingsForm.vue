<script setup lang="ts">
import type { HTMLAttributes } from 'vue'
import { cn } from '@/lib/utils'
import { Button } from '@/components/ui/button'
import { Card, CardContent, CardDescription, CardHeader, CardTitle } from '@/components/ui/card'
import { Input } from '@/components/ui/input'
import { useForm } from 'vee-validate'
import { toTypedSchema } from '@vee-validate/zod'
import * as z from 'zod'
import { FormControl, FormField, FormItem, FormLabel, FormMessage } from '@/components/ui/form'

const formSchema = toTypedSchema(
  z
    .object({
      firstName: z.string().min(2, 'First name must be at least 2 characters'),
      lastName: z.string().min(2, 'Last name must be at least 2 characters'),
      email: z.string().email('Please enter a valid email address'),
      username: z.string().min(3, 'Username must be at least 3 characters'),
      currentPassword: z.string().optional(),
      newPassword: z.string().min(8, 'Password must be at least 8 characters').optional(),
      confirmPassword: z.string().optional(),
      bio: z.string().max(500, 'Bio must be less than 500 characters').optional(),
      website: z.string().url('Please enter a valid URL').optional().or(z.literal('')),
    })
    .refine(
      (data) => {
        if (data.newPassword && !data.currentPassword) {
          return false
        }
        if (data.newPassword && data.newPassword !== data.confirmPassword) {
          return false
        }
        return true
      },
      {
        message: "Passwords don't match or current password is required",
        path: ['confirmPassword'],
      },
    ),
)

const form = useForm({
  validationSchema: formSchema,
  initialValues: {
    firstName: 'John',
    lastName: 'Doe',
    email: 'john.doe@example.com',
    username: 'johndoe',
    currentPassword: '',
    newPassword: '',
    confirmPassword: '',
    bio: '',
    website: '',
  },
})

const props = defineProps<{
  class?: HTMLAttributes['class']
}>()

const handleSubmit = form.handleSubmit((values) => {
  console.log('Settings updated!', values)
  // Here you would typically send the data to your API
})
</script>

<template>
  <div :class="cn('flex flex-col gap-6', props.class)">
    <Card>
      <CardHeader>
        <CardTitle>Account Settings</CardTitle>
        <CardDescription>Update your account information and preferences</CardDescription>
      </CardHeader>
      <CardContent>
        <form @submit="handleSubmit">
          <div class="flex flex-col gap-6">
            <!-- Personal Information Section -->
            <div class="space-y-4">
              <h3 class="text-lg font-medium">Personal Information</h3>

              <div class="grid grid-cols-1 md:grid-cols-2 gap-4">
                <FormField v-slot="{ componentField }" name="firstName">
                  <FormItem>
                    <FormLabel>First Name</FormLabel>
                    <FormControl>
                      <Input type="text" v-bind="componentField" />
                    </FormControl>
                    <FormMessage />
                  </FormItem>
                </FormField>

                <FormField v-slot="{ componentField }" name="lastName">
                  <FormItem>
                    <FormLabel>Last Name</FormLabel>
                    <FormControl>
                      <Input type="text" v-bind="componentField" />
                    </FormControl>
                    <FormMessage />
                  </FormItem>
                </FormField>
              </div>

              <FormField v-slot="{ componentField }" name="email">
                <FormItem>
                  <FormLabel>Email</FormLabel>
                  <FormControl>
                    <Input type="email" v-bind="componentField" />
                  </FormControl>
                  <FormMessage />
                </FormItem>
              </FormField>

              <FormField v-slot="{ componentField }" name="username">
                <FormItem>
                  <FormLabel>Username</FormLabel>
                  <FormControl>
                    <Input type="text" v-bind="componentField" />
                  </FormControl>
                  <FormMessage />
                </FormItem>
              </FormField>

              <FormField v-slot="{ componentField }" name="bio">
                <FormItem>
                  <FormLabel>Bio</FormLabel>
                  <FormControl>
                    <textarea
                      v-bind="componentField"
                      class="flex min-h-[80px] w-full rounded-md border border-input bg-background px-3 py-2 text-sm ring-offset-background placeholder:text-muted-foreground focus-visible:outline-none focus-visible:ring-2 focus-visible:ring-ring focus-visible:ring-offset-2 disabled:cursor-not-allowed disabled:opacity-50"
                      placeholder="Tell us a little about yourself..."
                    />
                  </FormControl>
                  <FormMessage />
                </FormItem>
              </FormField>

              <FormField v-slot="{ componentField }" name="website">
                <FormItem>
                  <FormLabel>Website</FormLabel>
                  <FormControl>
                    <Input type="url" placeholder="https://example.com" v-bind="componentField" />
                  </FormControl>
                  <FormMessage />
                </FormItem>
              </FormField>
            </div>

            <!-- Password Change Section -->
            <div class="space-y-4 pt-6 border-t">
              <h3 class="text-lg font-medium">Change Password</h3>
              <p class="text-sm text-muted-foreground">
                Leave blank if you don't want to change your password
              </p>

              <FormField v-slot="{ componentField }" name="currentPassword">
                <FormItem>
                  <FormLabel>Current Password</FormLabel>
                  <FormControl>
                    <Input type="password" v-bind="componentField" />
                  </FormControl>
                  <FormMessage />
                </FormItem>
              </FormField>

              <div class="grid grid-cols-1 md:grid-cols-2 gap-4">
                <FormField v-slot="{ componentField }" name="newPassword">
                  <FormItem>
                    <FormLabel>New Password</FormLabel>
                    <FormControl>
                      <Input type="password" v-bind="componentField" />
                    </FormControl>
                    <FormMessage />
                  </FormItem>
                </FormField>

                <FormField v-slot="{ componentField }" name="confirmPassword">
                  <FormItem>
                    <FormLabel>Confirm New Password</FormLabel>
                    <FormControl>
                      <Input type="password" v-bind="componentField" />
                    </FormControl>
                    <FormMessage />
                  </FormItem>
                </FormField>
              </div>
            </div>

            <!-- Action Buttons -->
            <div class="flex flex-col sm:flex-row gap-3 pt-6">
              <Button type="submit" class="w-full sm:w-auto"> Save Changes </Button>
              <Button type="button" variant="outline" class="w-full sm:w-auto"> Cancel </Button>
            </div>
          </div>
        </form>
      </CardContent>
    </Card>
  </div>
</template>
