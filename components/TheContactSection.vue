<template>
  <div
    ref="contactRef"
    class="bg-mirage-950 text-white min-h-screen px-10 py-40 grid place-content-center w-full"
  >
    <div
      class="flex flex-col items-center justify-center gap-y-10"
      v-motion-slide-visible-bottom
    >
      <h1 class="text-6xl text-center font-semibold">
        Contact <span class="text-primary">Me</span>
      </h1>
      <p
        class="max-w-[700px] text-gray-400 text-center text-sm leading-loose md:text-md"
      >
        In need of a developer with these kind of skill sets? Or need someone to
        manage your projects? Just reach out to me through my email and social
        media accounts.
      </p>
      <div class="space-y-5">
        <div v-for="contact in contacts" class="text-center">
          <div class="flex items-center justify-center gap-x-1 text-primary">
            <UIcon :name="contact.icon" class="text-lg" dynamic />
            <h2 class="align-middle">{{ contact.platform }}</h2>
          </div>
          <h2>{{ contact.detail }}</h2>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup lang="ts">
const contactRef = ref<HTMLElement | null>(null);

defineExpose({
  contactRef,
});

const contacts = [
  {
    platform: 'Gmail',
    icon: 'i-mdi-gmail',
    detail: 'pcmpardo@gmail.com',
  },
  {
    platform: 'Github',
    icon: 'i-mdi-github',
    detail: 'https://github.com/peterpardo',
  },
  {
    platform: 'Linkedin',
    icon: 'i-mdi-linkedin',
    detail: 'https://www.linkedin.com/in/pcmpardo/',
  },
];
</script>
