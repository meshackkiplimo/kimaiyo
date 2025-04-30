<template>
  <div class="pt-16">
    <section class="section">
      <div class="container">
        <h1 class="heading text-center">Skills & Expertise</h1>
        <p class="mt-4 text-center text-lg text-gray-600 dark:text-gray-400">
          A comprehensive overview of my technical skills and expertise
        </p>

        <!-- Skill Categories -->
        <div class="mt-16 grid gap-12">
          <div v-for="category in skillCategories" :key="category.name">
            <h2 class="text-2xl font-bold text-gray-900 dark:text-white">
              {{ category.name }}
            </h2>
            <p class="mt-2 text-gray-600 dark:text-gray-400">
              {{ category.description }}
            </p>

            <div class="mt-6 grid gap-6 sm:grid-cols-2">
              <div
                v-for="skill in category.skills"
                :key="skill.name"
                class="rounded-lg bg-white p-6 shadow-lg dark:bg-gray-800"
              >
                <div class="flex items-center justify-between">
                  <h3 class="text-lg font-semibold text-gray-900 dark:text-white">
                    {{ skill.name }}
                  </h3>
                  <span class="text-sm text-gray-500 dark:text-gray-400">
                    {{ skill.level }}
                  </span>
                </div>

                <!-- Progress Bar -->
                <div class="mt-4 h-2 rounded-full bg-gray-200 dark:bg-gray-700">
                  <div
                    class="h-2 rounded-full bg-primary-600 transition-all duration-500"
                    :style="{ width: `${skill.percentage}%` }"
                  ></div>
                </div>

                <p class="mt-4 text-sm text-gray-600 dark:text-gray-400">
                  {{ skill.description }}
                </p>

                <!-- Projects Using This Skill -->
                <div v-if="skill.projects?.length" class="mt-4">
                  <h4 class="text-sm font-medium text-gray-700 dark:text-gray-300">
                    Related Projects:
                  </h4>
                  <div class="mt-2 flex flex-wrap gap-2">
                    <NuxtLink
                      v-for="project in skill.projects"
                      :key="project"
                      to="/projects"
                      class="text-sm text-primary-600 hover:text-primary-700 dark:text-primary-400 dark:hover:text-primary-300"
                    >
                      {{ project }}
                    </NuxtLink>
                  </div>
                </div>
              </div>
            </div>
          </div>
        </div>

        <!-- Additional Skills -->
        <div class="mt-16">
          <h2 class="text-2xl font-bold text-gray-900 dark:text-white">
            Additional Skills
          </h2>
          <div class="mt-6 flex flex-wrap gap-2">
            <span
              v-for="skill in additionalSkills"
              :key="skill"
              class="rounded-full bg-gray-100 px-4 py-2 text-sm font-medium text-gray-800 dark:bg-gray-700 dark:text-gray-300"
            >
              {{ skill }}
            </span>
          </div>
        </div>
      </div>
    </section>
  </div>
</template>

<script setup lang="ts">
interface Skill {
  name: string
  level: string
  percentage: number
  description: string
  projects?: string[]
}

interface SkillCategory {
  name: string
  description: string
  skills: Skill[]
}

const skillCategories: SkillCategory[] = [
  {
    name: 'Frontend Development',
    description: 'Building responsive and interactive user interfaces with modern frameworks and tools',
    skills: [
      {
        name: 'Vue.js / Nuxt.js',
        level: 'Expert',
        percentage: 95,
        description: 'Advanced state management, custom components, and performance optimization',
        projects: ['E-commerce Platform', 'Portfolio Website'],
      },
      {
        name: 'React',
        level: 'Advanced',
        percentage: 85,
        description: 'Complex component architecture and Redux state management',
        projects: ['Task Management App'],
      },
      {
        name: 'TypeScript',
        level: 'Advanced',
        percentage: 90,
        description: 'Type-safe development with advanced features and patterns',
      },
      {
        name: 'CSS / TailwindCSS',
        level: 'Expert',
        percentage: 95,
        description: 'Responsive design, animations, and custom design systems',
      },
    ],
  },
  {
    name: 'Backend Development',
    description: 'Creating scalable server-side applications and APIs',
    skills: [
      {
        name: 'Node.js',
        level: 'Expert',
        percentage: 90,
        description: 'RESTful APIs, authentication, and real-time applications',
        projects: ['E-commerce Platform'],
      },
      {
        name: 'Python',
        level: 'Advanced',
        percentage: 85,
        description: 'Django and FastAPI development, data processing',
      },
      {
        name: 'Database Design',
        level: 'Advanced',
        percentage: 85,
        description: 'Schema design, optimization, and query performance',
      },
    ],
  },
  {
    name: 'DevOps & Tools',
    description: 'Managing deployment, infrastructure, and development workflows',
    skills: [
      {
        name: 'Docker',
        level: 'Advanced',
        percentage: 80,
        description: 'Containerization and multi-container applications',
      },
      {
        name: 'Git & CI/CD',
        level: 'Expert',
        percentage: 90,
        description: 'Version control, automated testing, and deployment',
      },
    ],
  },
]

const additionalSkills = [
  'AWS',
  'GraphQL',
  'Jest',
  'Cypress',
  'MongoDB',
  'PostgreSQL',
  'Redis',
  'WebSocket',
  'RESTful APIs',
  'Agile Methodologies',
  'UI/UX Design',
  'Performance Optimization',
]
</script>