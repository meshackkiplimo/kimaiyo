<template>
  <div class="min-h-screen bg-gray-50 dark:bg-gray-900">
    <!-- Navigation -->
    <nav class="fixed top-0 z-50 w-full bg-white/80 backdrop-blur dark:bg-gray-900/80">
      <div class="container flex h-16 items-center justify-between">
        <NuxtLink to="/" class="text-xl font-bold text-gray-900 dark:text-white">
          Meshack Kimaiyo
        </NuxtLink>
        <!-- Desktop Navigation -->
        <div class="hidden md:flex items-center gap-6">
          <NuxtLink
            v-for="item in navigation"
            :key="item.name"
            :to="item.href"
            class="text-sm font-medium text-gray-700 hover:text-gray-900 dark:text-gray-300 dark:hover:text-white"
          >
            {{ item.name }}
          </NuxtLink>
        </div>
        <!-- Mobile Menu Button -->
        <button 
          @click="mobileMenuOpen = !mobileMenuOpen" 
          class="md:hidden rounded-md p-2 text-gray-700 hover:bg-gray-100 dark:text-gray-300 dark:hover:bg-gray-800"
        >
          <span class="sr-only">Open menu</span>
          <svg 
            class="h-6 w-6" 
            fill="none" 
            viewBox="0 0 24 24" 
            stroke="currentColor"
          >
            <path 
              v-if="!mobileMenuOpen" 
              stroke-linecap="round" 
              stroke-linejoin="round" 
              stroke-width="2" 
              d="M4 6h16M4 12h16M4 18h16"
            />
            <path 
              v-else 
              stroke-linecap="round" 
              stroke-linejoin="round" 
              stroke-width="2" 
              d="M6 18L18 6M6 6l12 12"
            />
          </svg>
        </button>
      </div>
    </nav>

    <!-- Mobile Navigation Menu -->
    <div 
      v-if="mobileMenuOpen" 
      class="fixed inset-0 z-40 md:hidden"
    >
      <div 
        class="fixed inset-0 bg-black/25 backdrop-blur-sm"
        @click="mobileMenuOpen = false"
      ></div>
      <div class="fixed inset-y-0 right-0 w-full max-w-xs bg-white dark:bg-gray-900 shadow-xl">
        <div class="flex flex-col h-full pt-16 pb-6">
          <div class="px-4 space-y-1">
            <NuxtLink
              v-for="item in navigation"
              :key="item.name"
              :to="item.href"
              @click="mobileMenuOpen = false"
              class="block px-3 py-2 text-base font-medium text-gray-700 hover:bg-gray-100 dark:text-gray-300 dark:hover:bg-gray-800 rounded-md"
            >
              {{ item.name }}
            </NuxtLink>
          </div>
        </div>
      </div>
    </div>

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

const mobileMenuOpen = ref(false)
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
