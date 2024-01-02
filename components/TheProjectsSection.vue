<template>
  <div class="min-h-screen px-10 pt-40 grid place-content-center w-full">
    <div class="flex flex-col items-center justify-center gap-y-10">
      <h1 class="text-6xl text-center font-semibold">
        My <span class="text-primary">Projects</span>
      </h1>
      <p
        class="max-w-[700px] text-gray-400 text-center text-sm leading-loose md:text-md"
      >
        Here are some of my projects that I back when I was in college up to
        now. Most of theses project were deployed in Vercel. Some of them are
        just screenshots when I ran it in my local machine.
      </p>

      <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-5">
        <UCard
          v-for="(project, index) in projects"
          :key="index"
          class="w-72 mx-auto md:w-74 md:mx-0"
          :ui="{
            body: { base: 'flex flex-col h-full', padding: 'p-0 sm:p-0' },
          }"
        >
          <div>
            <img :src="project.image" :alt="project.name" />
          </div>

          <div class="p-4 space-y-4">
            <h2 class="font-semibold text-lg">{{ project.name }}</h2>
            <p class="text-gray-400">
              {{ project.description }}
            </p>
          </div>

          <div class="flex gap-x-2 justify-end items-center mt-auto p-4">
            <UButton color="gray" :to="project.githubLink" target="_blank">
              <UIcon name="i-mdi-github" dynamic  class="text-lg"/>
              Code
            </UButton>
            <UButton
              v-if="project?.demoLink"
              :to="project?.demoLink"
              target="_blank"
            >
              <UIcon name="i-mdi-monitor" dynamic />
              Demo
            </UButton>
          </div>
        </UCard>
      </div>
    </div>
  </div>
</template>

<script setup lang="ts">
const projects = [
  {
    name: 'Threads Clone',
    description: 'This was made using Nuxt, Tailwindcss, Prisma, and Supabase.',
    image: '/images/threads-clone.png',
    githubLink: 'https://github.com/peterpardo/threads-clone',
    demoLink: 'https://threads-clone-wheat-eight.vercel.app/',
  },
  {
    name: 'Custom Laravel Authentication',
    description:
      'I was learning how to manually create an authentication without using a package in Laravel',
    image: '/images/laravel-custom-auth-img.png',
    githubLink: 'https://github.com/peterpardo/laravel-custom-auth',
  },
  {
    name: 'IP Address Tracker',
    description: 'Created using Reactjs. Added maps in a website.',
    image: '/images/ip-address-tracker-img.png',
    githubLink: 'https://github.com/peterpardo/ip-address-tracker',
    demoLink: 'https://ip-address-tracker-xi-nine.vercel.app/',
  },
  {
    name: 'REST Countries API',
    description:
      'Created using Reactjs. First time to call an API in the frontend',
    image: '/images/rest-countries-api-img.png',
    githubLink: 'https://github.com/peterpardo/rest-countries-api',
    demoLink: 'https://rest-countries-api-opal.vercel.app/',
  },
];
</script>
