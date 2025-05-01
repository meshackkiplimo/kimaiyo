<template>
  <div class="pt-16">
    <section class="section">
      <div class="container">
        <h1 class="heading text-center">Featured Projects</h1>
        <p class="mt-4 text-center text-lg text-gray-600 dark:text-gray-400">
          Highlighting my most impactful work
        </p>

        <!-- Featured Projects -->
        <div class="mt-12 grid gap-8 lg:grid-cols-2">
          <div
            v-for="project in featuredProjects"
            :key="project.title"
            class="group relative flex flex-col overflow-hidden rounded-lg bg-white shadow-lg transition-transform hover:-translate-y-1 dark:bg-gray-800">
            <div class="aspect-h-9 aspect-w-16 relative overflow-hidden">
              <NuxtImg
                :src="project.image"
                :alt="project.title"
                class="object-cover transition-transform duration-300 group-hover:scale-105" />
              <div class="absolute inset-0 bg-gradient-to-t from-gray-900/75 to-transparent"></div>
            </div>
            <div class="flex flex-1 flex-col p-6">
              <h3 class="text-xl font-semibold text-gray-900 dark:text-white">{{ project.title }}</h3>
              <p class="mt-2 flex-1 text-gray-600 dark:text-gray-400">{{ project.description }}</p>
              <div class="mt-4 flex flex-wrap gap-2">
                <span
                  v-for="tech in project.technologies"
                  :key="tech"
                  class="rounded-full bg-gray-100 px-3 py-1 text-sm text-gray-800 dark:bg-gray-700 dark:text-gray-300">
                  {{ tech }}
                </span>
              </div>
              <div class="mt-6 flex gap-4">
                <a
                  v-if="project.demoUrl"
                  :href="project.demoUrl"
                  target="_blank"
                  rel="noopener"
                  class="btn btn-primary flex-1">
                  Live Demo
                </a>
                <a
                  v-if="project.githubUrl"
                  :href="project.githubUrl"
                  target="_blank"
                  rel="noopener"
                  class="flex-1 rounded-md border border-gray-300 px-4 py-2 text-center font-semibold text-gray-700 transition-colors hover:bg-gray-50 dark:border-gray-600 dark:text-gray-300 dark:hover:bg-gray-700">
                  View Code
                </a>
              </div>
            </div>
          </div>
        </div>

        <h2 class="heading mt-20 text-center text-2xl">Other Projects</h2>
        
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
            ]">
            {{ tag }}
          </button>
        </div>

        <!-- Other Projects Grid -->
        <div class="mt-12 grid gap-8 sm:grid-cols-2 lg:grid-cols-3">
          <div
            v-for="project in filteredNonFeaturedProjects"
            :key="project.title"
            class="group relative flex flex-col overflow-hidden rounded-lg bg-white shadow-lg transition-transform hover:-translate-y-1 dark:bg-gray-800">
            <div class="aspect-h-9 aspect-w-16 relative overflow-hidden">
              <NuxtImg
                :src="project.image"
                :alt="project.title"
                class="object-cover transition-transform duration-300 group-hover:scale-105" />
              <div class="absolute inset-0 bg-gradient-to-t from-gray-900/75 to-transparent"></div>
            </div>
            <div class="flex flex-1 flex-col p-6">
              <h3 class="text-xl font-semibold text-gray-900 dark:text-white">{{ project.title }}</h3>
              <p class="mt-2 flex-1 text-gray-600 dark:text-gray-400">{{ project.description }}</p>
              <div class="mt-4 flex flex-wrap gap-2">
                <span
                  v-for="tech in project.technologies"
                  :key="tech"
                  class="rounded-full bg-gray-100 px-3 py-1 text-sm text-gray-800 dark:bg-gray-700 dark:text-gray-300">
                  {{ tech }}
                </span>
              </div>
              <div class="mt-6 flex gap-4">
                <a
                  v-if="project.demoUrl"
                  :href="project.demoUrl"
                  target="_blank"
                  rel="noopener"
                  class="btn btn-primary flex-1">
                  Live Demo
                </a>
                <a
                  v-if="project.githubUrl"
                  :href="project.githubUrl"
                  target="_blank"
                  rel="noopener"
                  class="flex-1 rounded-md border border-gray-300 px-4 py-2 text-center font-semibold text-gray-700 transition-colors hover:bg-gray-50 dark:border-gray-600 dark:text-gray-300 dark:hover:bg-gray-700">
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
  featured?: boolean
}

const selectedTags = ref<string[]>([])

const projects: Project[] = [
  {
    title: 'Kuuku - Chicken Management System',
    description: 'A comprehensive farm management system designed specifically for poultry farmers, helping them track chicken health, production, and inventory.',
    image: '/img/kuuku.JPG',
    technologies: ['Vue.js', 'Node.js', 'MongoDB', 'Farm Management'],
    demoUrl: 'https://fanya-theta.vercel.app/',
    featured: true
  },
  {
    title: 'Gateway - Hospital Management System',
    description: 'A comprehensive hospital management system for streamlining patient care, appointments, and medical records management.',
    image: '/img/gateway.JPG',
    technologies: ['React', 'Node.js', 'MongoDB', 'Healthcare'],
    demoUrl: 'https://gateway-steel-six.vercel.app/',
    featured: true
  },
  {
    title: 'Surv - Survey Application',
    description: 'A versatile survey application for creating, distributing, and analyzing survey data with real-time analytics and reporting features.',
    image: '/img/surv.JPG',
    technologies: ['React', 'Express', 'PostgreSQL', 'Analytics'],
    demoUrl: 'https://surveyapp-topaz.vercel.app/'
  },
  {
    title: 'Azura - Psychological Guidance Platform',
    description: 'A confidential consultation and psychological guidance platform connecting users with mental health professionals.',
    image: '/img/azura.JPG',
    technologies: ['Vue.js', 'Node.js', 'MongoDB', 'Healthcare'],
    demoUrl: 'https://azzuracom.vercel.app/'
  },
  {
    title: 'Kokya Foundation',
    description: 'Corporate website for Kokya Foundation showcasing the organization\'s mission, projects, and impact in the community.',
    image: '/img/kokya.JPG',
    technologies: ['Nuxt.js', 'TailwindCSS', 'Corporate'],
    demoUrl: 'https://kokya-foundation.vercel.app/'
  },
  {
    title: 'Pesa - Cash Management System',
    description: 'A robust financial management platform for tracking expenses, managing budgets, and generating financial reports.',
    image: '/img/pesa.JPG',
    technologies: ['Vue.js', 'Express', 'PostgreSQL', 'Finance'],
    demoUrl: 'https://pesa-cash.vercel.app/'
  }
]

const featuredProjects = computed(() => 
  projects.filter(project => project.featured)
)

const nonFeaturedProjects = computed(() => 
  projects.filter(project => !project.featured)
)

const uniqueTags = computed(() => {
  const tags = new Set<string>()
  nonFeaturedProjects.value.forEach(project => {
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

const filteredNonFeaturedProjects = computed(() => {
  if (selectedTags.value.length === 0) return nonFeaturedProjects.value
  return nonFeaturedProjects.value.filter(project =>
    selectedTags.value.every(tag => project.technologies.includes(tag))
  )
})
</script>