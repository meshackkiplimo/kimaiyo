<template>
  <div class="pt-16">
    <!-- Bio Section -->
    <section class="section">
      <div class="container">
        <div class="mx-auto max-w-4xl">
          <h1 class="heading text-center">About Me</h1>
          <div class="mt-12 flex flex-col md:flex-row gap-12 items-start">
            <div class="md:w-1/3 mx-auto">
              <div class="w-60 h-72 rounded-lg overflow-hidden shadow-xl">
                <img src="/img/image 2.jpg" alt="Professional Photo" class="w-full h-full object-cover" />
              </div>
            </div>
            <div class="md:w-2/3 space-y-6 text-lg text-gray-600 dark:text-gray-400">
              <p>
                Hi! I'm a passionate Full Stack Developer with a strong foundation in modern web technologies. 
                I specialize in building scalable web applications and creating exceptional user experiences.
              </p>
              <p>
                With several years of experience in software development, I've worked on various projects 
                ranging from e-commerce platforms to real-time collaboration tools. I'm constantly learning 
                and staying up-to-date with the latest technologies and best practices.
              </p>
              <p>
                When I'm not coding, you can find me contributing to open-source projects, writing technical 
                blog posts, or mentoring aspiring developers.
              </p>
            </div>
          </div>
        </div>
      </div>
    </section>

    <!-- Experience Timeline -->
    <section class="section bg-gray-50 dark:bg-gray-800/50">
      <div class="container">
        <h2 class="heading text-center">Experience</h2>
        <div class="mt-12 max-w-3xl mx-auto">
          <div v-for="(experience, index) in experiences" :key="index" 
               class="relative pl-8 pb-12 last:pb-0">
            <!-- Timeline line -->
            <div class="absolute left-0 top-0 bottom-0 w-px bg-primary-200 dark:bg-primary-800"></div>
            <!-- Timeline dot -->
            <div class="absolute left-[-4px] top-2 h-2 w-2 rounded-full bg-primary-600"></div>
            
            <div class="space-y-2">
              <h3 class="font-semibold text-xl text-gray-900 dark:text-white">
                {{ experience.role }}
              </h3>
              <div class="text-primary-600 dark:text-primary-400 font-medium">
                {{ experience.company }}
              </div>
              <div class="text-sm text-gray-500 dark:text-gray-400">
                {{ experience.period }}
              </div>
              <ul class="mt-4 list-disc pl-4 space-y-2 text-gray-600 dark:text-gray-400">
                <li v-for="(achievement, i) in experience.achievements" :key="i">
                  {{ achievement }}
                </li>
              </ul>
            </div>
          </div>
        </div>
      </div>
    </section>

    <!-- Education Section -->
    <section class="section">
      <div class="container">
        <h2 class="heading text-center">Education</h2>
        <div class="mt-12 grid gap-8 sm:grid-cols-2 max-w-3xl mx-auto">
          <div v-for="education in educationList" :key="education.degree" 
               class="rounded-lg bg-white p-6 shadow-lg dark:bg-gray-800">
            <h3 class="font-semibold text-lg text-gray-900 dark:text-white">
              {{ education.degree }}
            </h3>
            <div class="mt-2 text-primary-600 dark:text-primary-400">
              {{ education.school }}
            </div>
            <div class="mt-1 text-sm text-gray-500 dark:text-gray-400">
              {{ education.period }}
            </div>
            <p class="mt-4 text-gray-600 dark:text-gray-400">
              {{ education.description }}
            </p>
          </div>
        </div>
      </div>
    </section>
  </div>
</template>

<script setup lang="ts">
const experiences = [
  {
    role: 'Software Engineering Intern',
    company: 'Teach2Give',
    period: 'May 2025 - Present',
    achievements: [
      'Currently participating in software engineering internship program',
      'Working on practical software development projects',
      'Learning and implementing modern development practices',
    ],
  },
  {
    role: 'Software Developer (Part-time)',
    company: 'Momi Foundation',
    period: 'October 2024 - Present',
    achievements: [
      'Developing and maintaining foundation software systems',
      'Contributing to various software development projects',
      'Working collaboratively in a part-time capacity',
    ],
  },
  {
    role: 'Software Engineering Intern',
    company: 'Taquana',
    period: 'May 2024 - August 2024',
    achievements: [
      'Completed summer internship program',
      'Gained practical experience in software development',
      'Contributed to company projects and initiatives',
    ],
  },
]

const educationList = [
  {
    degree: 'Bachelor of Science in Software Engineering',
    school: 'University of Eastern Africa Baraton',
    period: '2021 - 2025',
    description: 'Specializing in software development and engineering principles.',
  }
]
</script>