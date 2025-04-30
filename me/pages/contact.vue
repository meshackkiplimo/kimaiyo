<template>
  <div class="pt-16">
    <section class="section">
      <div class="container">
        <div class="mx-auto max-w-xl">
          <h1 class="heading text-center">Get in Touch</h1>
          <p class="mt-4 text-center text-lg text-gray-600 dark:text-gray-400">
            Feel free to reach out for collaborations or just a friendly hello
          </p>

          <!-- Contact Form -->
          <form @submit.prevent="handleSubmit" class="mt-12">
            <div class="space-y-6">
              <div>
                <label for="name" class="block text-sm font-medium text-gray-700 dark:text-gray-300">
                  Name
                </label>
                <input
                  type="text"
                  id="name"
                  v-model="form.name"
                  required
                  class="mt-1 block w-full rounded-md border-gray-300 shadow-sm focus:border-primary-500 focus:ring-primary-500 dark:border-gray-600 dark:bg-gray-800 dark:text-white"
                />
              </div>

              <div>
                <label for="email" class="block text-sm font-medium text-gray-700 dark:text-gray-300">
                  Email
                </label>
                <input
                  type="email"
                  id="email"
                  v-model="form.email"
                  required
                  class="mt-1 block w-full rounded-md border-gray-300 shadow-sm focus:border-primary-500 focus:ring-primary-500 dark:border-gray-600 dark:bg-gray-800 dark:text-white"
                />
              </div>

              <div>
                <label for="message" class="block text-sm font-medium text-gray-700 dark:text-gray-300">
                  Message
                </label>
                <textarea
                  id="message"
                  v-model="form.message"
                  rows="4"
                  required
                  class="mt-1 block w-full rounded-md border-gray-300 shadow-sm focus:border-primary-500 focus:ring-primary-500 dark:border-gray-600 dark:bg-gray-800 dark:text-white"
                ></textarea>
              </div>

              <div>
                <button
                  type="submit"
                  :disabled="isSubmitting"
                  class="w-full btn btn-primary flex items-center justify-center"
                >
                  <span v-if="isSubmitting">Sending...</span>
                  <span v-else>Send Message</span>
                </button>
              </div>
            </div>
          </form>

          <!-- Social Links -->
          <div class="mt-12">
            <h2 class="text-center text-xl font-semibold text-gray-900 dark:text-white">
              Connect with me
            </h2>
            <div class="mt-6 flex justify-center space-x-6">
              <a
                v-for="social in socials"
                :key="social.name"
                :href="social.url"
                target="_blank"
                rel="noopener noreferrer"
                class="text-gray-600 hover:text-primary-600 dark:text-gray-400 dark:hover:text-primary-400"
              >
                <span class="sr-only">{{ social.name }}</span>
                <Icon :name="social.icon" class="h-6 w-6" />
              </a>
            </div>
          </div>
        </div>
      </div>
    </section>
  </div>
</template>

<script setup lang="ts">
import { ref } from 'vue'

interface FormData {
  name: string
  email: string
  message: string
}

const form = ref<FormData>({
  name: '',
  email: '',
  message: '',
})

const isSubmitting = ref(false)

const socials = [
  {
    name: 'GitHub',
    url: 'https://github.com/yourusername',
    icon: 'mdi:github',
  },
  {
    name: 'LinkedIn',
    url: 'https://linkedin.com/in/yourusername',
    icon: 'mdi:linkedin',
  },
  {
    name: 'Twitter',
    url: 'https://twitter.com/yourusername',
    icon: 'mdi:twitter',
  },
]

const handleSubmit = async () => {
  isSubmitting.value = true
  try {
    // Here you would typically make an API call to your backend
    // For now, we'll simulate a delay
    await new Promise(resolve => setTimeout(resolve, 1000))
    alert('Message sent successfully!')
    form.value = {
      name: '',
      email: '',
      message: '',
    }
  } catch (error) {
    alert('Failed to send message. Please try again.')
  } finally {
    isSubmitting.value = false
  }
}
</script>