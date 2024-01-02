<template>
  <nav class="sticky top-0 bg-white bg-opacity-80 dark:bg-mirage-950">
    <UContainer
      class="w-full flex items-center justify-between px-10 py-5 md:py-5 dark:bg-mirage-950"
    >
      <div class="font-semibold text-2xl cursor-pointer">
        <span class="text-primary">P</span>P
      </div>

      <div class="hidden md:flex justify-between items-center gap-x-20">
        <div class="cursor-pointer hover:text-primary">Home</div>
        <div class="cursor-pointer hover:text-primary">Skills</div>
        <div class="cursor-pointer hover:text-primary">Projects</div>
        <div class="cursor-pointer hover:text-primary">Contact</div>
      </div>

      <div class="flex items-center justify-between gap-x-3">
        <ULink to="https://github.com/peterpardo" target="_blank">
          <UIcon
            class="text-2xl hover:text-primary cursor-pointer"
            name="i-mdi-github"
            dynamic
          />
        </ULink>
        <ULink to="https://www.linkedin.com/in/pcmpardo/" target="_blank">
          <UIcon
            class="text-2xl hover:text-primary cursor-pointer"
            name="i-mdi-linkedin"
            dynamic
          />
        </ULink>
        <UToggle v-model="isDarkMode" />
        <UButton
          class="block md:hidden ml-4"
          variant="ghost"
          color="black"
          @click="isMenuOpen = !isMenuOpen"
        >
          <UIcon
            v-if="!isMenuOpen"
            class="text-2xl"
            name="i-mdi-menu"
            dynamic
          />
          <UIcon
            v-else
            class="text-2xl align-middle"
            name="i-heroicons-x-mark"
          />
        </UButton>
      </div>

      <div
        v-if="isMenuOpen"
        class="absolute h-screen p-10 w-full z-10 top-20 left-0 bg-white dark:bg-mirage-950"
      >
        <ul>
          <li class="py-2 cursor-pointer hover:text-primary">Home</li>
          <li class="py-2 cursor-pointer hover:text-primary">Skills</li>
          <li class="py-2 cursor-pointer hover:text-primary">Projects</li>
          <li class="py-2 cursor-pointer hover:text-primary">Contact</li>
        </ul>
      </div>
    </UContainer>
  </nav>
</template>

<script setup lang="ts">
definePageMeta({
  colorMode: 'light',
});

const isDarkMode = ref(false);
const isMenuOpen = ref(false);
const windowWidth = ref(window?.innerWidth);
const colorMode = useColorMode();

watch(windowWidth, (newWindowWidth) => {
  if (newWindowWidth > 768) {
    isMenuOpen.value = false;
  }
});

watch(isDarkMode, (newIsDarkMode) => {
  if (newIsDarkMode) {
    colorMode.preference = 'dark';
  } else {
    colorMode.preference = 'light';
  }
});

onMounted(() => {
  const colorMode = localStorage.getItem('nuxt-color-mode');

  if (colorMode === 'dark') {
    isDarkMode.value = true;
  }

  window.addEventListener('resize', () => {
    windowWidth.value = window.innerWidth;
  });
});

onUnmounted(() => {
  window.removeEventListener('resize', () => {
    windowWidth.value = window.innerWidth;
  });
});
</script>
