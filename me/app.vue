<template>
  <div class="min-h-screen bg-gray-50 dark:bg-gray-900">
    <!-- Navigation -->
    <nav class="fixed top-0 z-50 w-full bg-white/80 backdrop-blur dark:bg-gray-900/80">
      <div class="container flex h-16 items-center justify-between">
        <NuxtLink to="/" class="text-xl font-bold text-gray-900 dark:text-white">
          Meshack Kimaiyo
        </NuxtLink>
        <div class="flex items-center gap-6">
          <NuxtLink
            v-for="item in navigation"
            :key="item.name"
            :to="item.href"
            class="text-sm font-medium text-gray-700 hover:text-gray-900 dark:text-gray-300 dark:hover:text-white"
          >
            {{ item.name }}
          </NuxtLink>
        </div>
      </div>
    </nav>

    <!-- Main Content -->
    <main class="pt-16">
      <NuxtPage />
    </main>

    <!-- Footer -->
    <footer class="mt-32 bg-gray-100 dark:bg-gray-800">
      <div class="container py-8">
        <p class="text-center text-sm text-gray-500 dark:text-gray-400">
          © {{ new Date().getFullYear() }} Your Name. All rights reserved.
        </p>
      </div>
    </footer>
  </div>
</template>

<script setup lang="ts">
const navigation = [
  { name: 'About', href: '/about' },
  { name: 'Projects', href: '/projects' },
  { name: 'Skills', href: '/skills' },
  { name: 'Contact', href: '/contact' },
]
</script>

<style>
.page-enter-active,
.page-leave-active {
  transition: all 0.2s;
}
.page-enter-from,
.page-leave-to {
  opacity: 0;
  transform: translateY(20px);
}
</style>
