<template>
  <div>
    <!-- Hero Section -->
    <section class="relative overflow-hidden bg-gray-900 py-32">
      <div class="container relative z-10">
        <div class="mx-auto max-w-2xl text-center">
          <h1 class="animate-fade-in text-4xl font-bold tracking-tight text-white sm:text-6xl">
            Full Stack Developer
          </h1>
          <p class="animate-slide-up mt-6 text-lg leading-8 text-gray-300">
            Building innovative web solutions with modern technologies
          </p>
          <div class="mt-10 flex items-center justify-center gap-x-6">
            <NuxtLink
              to="/projects"
              class="btn btn-primary"
            >
              View My Work
            </NuxtLink>
            <NuxtLink
              to="/contact"
              class="text-sm font-semibold leading-6 text-white"
            >
              Contact Me <span aria-hidden="true">→</span>
            </NuxtLink>
          </div>
        </div>
      </div>
      <div class="absolute inset-0 -z-10 bg-gradient-to-b from-gray-900 via-gray-900/40"></div>
    </section>

    <!-- Featured Projects Section -->
    <section class="section">
      <div class="container">
        <div class="mx-auto max-w-2xl text-center">
          <h2 class="heading">Featured Projects</h2>
          <p class="mt-4 text-lg text-gray-600 dark:text-gray-400">
            Check out some of my recent work
          </p>
        </div>
        <div class="mt-16 grid gap-8 sm:grid-cols-2 lg:grid-cols-3">
          <div v-for="project in featuredProjects" :key="project.title" 
               class="group relative overflow-hidden rounded-lg bg-white shadow-lg transition-transform hover:-translate-y-1 dark:bg-gray-800">
            <div class="aspect-h-9 aspect-w-16 overflow-hidden">
              <img :src="project.image" :alt="project.title" class="object-cover" />
            </div>
            <div class="p-6">
              <h3 class="text-xl font-semibold text-gray-900 dark:text-white">{{ project.title }}</h3>
              <p class="mt-2 text-gray-600 dark:text-gray-400">{{ project.description }}</p>
              <div class="mt-4 flex flex-wrap gap-2">
                <span v-for="tech in project.technologies" :key="tech"
                      class="rounded-full bg-gray-100 px-3 py-1 text-sm text-gray-800 dark:bg-gray-700 dark:text-gray-300">
                  {{ tech }}
                </span>
              </div>
            </div>
          </div>
        </div>
      </div>
    </section>

    <!-- Skills Section -->
    <section class="section bg-gray-50 dark:bg-gray-800/50">
      <div class="container">
        <div class="mx-auto max-w-2xl text-center">
          <h2 class="heading">Skills & Technologies</h2>
          <p class="mt-4 text-lg text-gray-600 dark:text-gray-400">
            Technologies I work with to bring ideas to life
          </p>
        </div>
        <div class="mt-16 grid gap-8 sm:grid-cols-2 lg:grid-cols-3">
          <div v-for="category in skills" :key="category.name" 
               class="rounded-xl bg-white p-6 shadow-lg dark:bg-gray-800">
            <h3 class="text-lg font-semibold text-gray-900 dark:text-white">
              {{ category.name }}
            </h3>
            <div class="mt-4 flex flex-wrap gap-2">
              <span v-for="skill in category.items" :key="skill"
                    class="rounded-full bg-primary-100 px-3 py-1 text-sm text-primary-800 dark:bg-primary-900/20 dark:text-primary-300">
                {{ skill }}
              </span>
            </div>
          </div>
        </div>
      </div>
    </section>
  </div>
</template>

<script setup lang="ts">
interface Project {
  title: string
  description: string
  image: string
  technologies: string[]
}

interface SkillCategory {
  name: string
  items: string[]
}

const featuredProjects: Project[] = [
  {
    title: 'E-commerce Platform',
    description: 'A modern e-commerce platform with real-time inventory management',
    image: '/projects/ecommerce.jpg',
    technologies: ['Vue.js', 'Node.js', 'MongoDB'],
  },
  {
    title: 'Task Management App',
    description: 'A collaborative task management application with real-time updates',
    image: '/projects/taskapp.jpg',
    technologies: ['React', 'Express', 'Socket.io'],
  },
  {
    title: 'Portfolio Website',
    description: 'A responsive portfolio website built with modern technologies',
    image: '/projects/portfolio.jpg',
    technologies: ['Nuxt.js', 'TailwindCSS', 'TypeScript'],
  },
]

const skills: SkillCategory[] = [
  {
    name: 'Frontend',
    items: ['Vue.js', 'React', 'TypeScript', 'TailwindCSS', 'HTML/CSS'],
  },
  {
    name: 'Backend',
    items: ['Node.js', 'Express', 'Python', 'Django', 'REST APIs'],
  },
  {
    name: 'Database',
    items: ['MongoDB', 'PostgreSQL', 'Redis', 'GraphQL'],
  },
  {
    name: 'DevOps',
    items: ['Docker', 'AWS', 'CI/CD', 'Git', 'Linux'],
  },
  {
    name: 'Tools & Methods',
    items: ['Agile', 'TDD', 'Version Control', 'Scrum'],
  },
  {
    name: 'Soft Skills',
    items: ['Problem Solving', 'Communication', 'Team Leadership', 'Mentoring'],
  },
]
</script>
