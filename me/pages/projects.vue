<template>
  <div class="pt-16">
    <section class="section">
      <div class="container">
        <h1 class="heading text-center">My Projects</h1>
        <p class="mt-4 text-center text-lg text-gray-600 dark:text-gray-400">
          A collection of my work and personal projects
        </p>

        <!-- Filter Tags -->
        <div class="mt-8 flex flex-wrap justify-center gap-2">
          <button
            v-for="tag in uniqueTags"
            :key="tag"
            @click="toggleTag(tag)"
            :class="[
              'rounded-full px-4 py-2 text-sm font-medium transition-colors',
              selectedTags.includes(tag)
                ? 'bg-primary-600 text-white'
                : 'bg-gray-100 text-gray-800 hover:bg-gray-200 dark:bg-gray-800 dark:text-gray-200 dark:hover:bg-gray-700'
            ]"
          >
            {{ tag }}
          </button>
        </div>

        <!-- Projects Grid -->
        <div class="mt-12 grid gap-8 sm:grid-cols-2 lg:grid-cols-3">
          <div
            v-for="project in filteredProjects"
            :key="project.title"
            class="group relative flex flex-col overflow-hidden rounded-lg bg-white shadow-lg transition-transform hover:-translate-y-1 dark:bg-gray-800"
          >
            <div class="aspect-h-9 aspect-w-16 relative overflow-hidden">
              <img
                :src="project.image"
                :alt="project.title"
                class="object-cover transition-transform duration-300 group-hover:scale-105"
              />
              <div class="absolute inset-0 bg-gradient-to-t from-gray-900/75 to-transparent"></div>
            </div>
            
            <div class="flex flex-1 flex-col p-6">
              <h3 class="text-xl font-semibold text-gray-900 dark:text-white">
                {{ project.title }}
              </h3>
              <p class="mt-2 flex-1 text-gray-600 dark:text-gray-400">
                {{ project.description }}
              </p>
              
              <div class="mt-4 flex flex-wrap gap-2">
                <span
                  v-for="tech in project.technologies"
                  :key="tech"
                  class="rounded-full bg-gray-100 px-3 py-1 text-sm text-gray-800 dark:bg-gray-700 dark:text-gray-300"
                >
                  {{ tech }}
                </span>
              </div>

              <div class="mt-6 flex gap-4">
                <a
                  v-if="project.demoUrl"
                  :href="project.demoUrl"
                  target="_blank"
                  rel="noopener"
                  class="btn btn-primary flex-1"
                >
                  Live Demo
                </a>
                <a
                  v-if="project.githubUrl"
                  :href="project.githubUrl"
                  target="_blank"
                  rel="noopener"
                  class="flex-1 rounded-md border border-gray-300 px-4 py-2 text-center font-semibold text-gray-700 transition-colors hover:bg-gray-50 dark:border-gray-600 dark:text-gray-300 dark:hover:bg-gray-700"
                >
                  View Code
                </a>
              </div>
            </div>
          </div>
        </div>
      </div>
    </section>
  </div>
</template>

<script setup lang="ts">
import { ref, computed } from 'vue'

interface Project {
  title: string
  description: string
  image: string
  technologies: string[]
  demoUrl?: string
  githubUrl?: string
}

const selectedTags = ref<string[]>([])

const projects: Project[] = [
  {
    title: 'E-commerce Platform',
    description: 'A full-featured e-commerce platform with real-time inventory management, payment processing, and admin dashboard.',
    image: '/projects/ecommerce.jpg',
    technologies: ['Vue.js', 'Node.js', 'MongoDB', 'Socket.io'],
    demoUrl: 'https://ecommerce-demo.com',
    githubUrl: 'https://github.com/username/ecommerce',
  },
  {
    title: 'Task Management App',
    description: 'A collaborative task management application with real-time updates, file sharing, and team chat features.',
    image: '/projects/taskapp.jpg',
    technologies: ['React', 'Express', 'PostgreSQL', 'WebSocket'],
    demoUrl: 'https://taskapp-demo.com',
    githubUrl: 'https://github.com/username/taskapp',
  },
  {
    title: 'Portfolio Website',
    description: 'A responsive portfolio website built with modern technologies and animations.',
    image: '/projects/portfolio.jpg',
    technologies: ['Nuxt.js', 'TailwindCSS', 'TypeScript'],
    githubUrl: 'https://github.com/username/portfolio',
  },
  {
    title: 'Weather Dashboard',
    description: 'Real-time weather monitoring dashboard with interactive maps and historical data visualization.',
    image: '/projects/weather.jpg',
    technologies: ['Vue.js', 'D3.js', 'APIs', 'Chart.js'],
    demoUrl: 'https://weather-dash.com',
    githubUrl: 'https://github.com/username/weather',
  },
]

const uniqueTags = computed(() => {
  const tags = new Set<string>()
  projects.forEach(project => {
    project.technologies.forEach(tech => tags.add(tech))
  })
  return Array.from(tags).sort()
})

const toggleTag = (tag: string) => {
  const index = selectedTags.value.indexOf(tag)
  if (index === -1) {
    selectedTags.value.push(tag)
  } else {
    selectedTags.value.splice(index, 1)
  }
}

const filteredProjects = computed(() => {
  if (selectedTags.value.length === 0) return projects
  return projects.filter(project =>
    selectedTags.value.every(tag => project.technologies.includes(tag))
  )
})
</script>