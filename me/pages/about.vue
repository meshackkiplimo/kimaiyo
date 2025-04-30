<template>
  <div class="pt-16">
    <!-- Bio Section -->
    <section class="section">
      <div class="container">
        <div class="mx-auto max-w-3xl">
          <h1 class="heading text-center">About Me</h1>
          <div class="mt-8 space-y-6 text-lg text-gray-600 dark:text-gray-400">
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
    role: 'Senior Full Stack Developer',
    company: 'Tech Solutions Inc.',
    period: '2021 - Present',
    achievements: [
      'Led development of microservices-based architecture, improving system scalability by 300%',
      'Mentored junior developers and established coding standards',
      'Implemented CI/CD pipeline reducing deployment time by 60%',
    ],
  },
  {
    role: 'Full Stack Developer',
    company: 'Digital Innovations',
    period: '2019 - 2021',
    achievements: [
      'Developed and maintained multiple client projects using Vue.js and Node.js',
      'Optimized database queries resulting in 40% faster load times',
      'Implemented real-time features using WebSocket technology',
    ],
  },
  {
    role: 'Frontend Developer',
    company: 'Web Creators Co.',
    period: '2017 - 2019',
    achievements: [
      'Built responsive web applications using React and Redux',
      'Collaborated with UX team to implement pixel-perfect designs',
      'Reduced bundle size by 45% through code splitting and lazy loading',
    ],
  },
]

const educationList = [
  {
    degree: 'Master of Science in Computer Science',
    school: 'Tech University',
    period: '2015 - 2017',
    description: 'Specialized in Software Engineering and Distributed Systems. Graduated with honors.',
  },
  {
    degree: 'Bachelor of Science in Computer Science',
    school: 'State University',
    period: '2011 - 2015',
    description: 'Focus on Web Development and Database Management. Dean\'s List recipient.',
  },
]
</script>