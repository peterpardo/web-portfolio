<template>
  <nav
    :class="{
      'bg-opacity-95': !isMenuOpen,
    }"
    class="sticky top-0 bg-white dark:bg-mirage-950"
  >
    <UContainer
      class="w-full flex items-center justify-between px-10 py-5 md:py-5 dark:bg-mirage-950"
    >
      <div
        class="font-semibold text-2xl cursor-pointer"
        @click="$emit('scroll-to', 'home')"
      >
        <span class="text-primary">P</span>P
      </div>

      <div class="hidden md:flex justify-between items-center gap-x-20">
        <div
          class="cursor-pointer hover:text-primary"
          @click="$emit('scroll-to', 'home')"
        >
          Home
        </div>
        <div
          class="cursor-pointer hover:text-primary"
          @click="$emit('scroll-to', 'skills')"
        >
          Skills
        </div>
        <div
          class="cursor-pointer hover:text-primary"
          @click="$emit('scroll-to', 'projects')"
        >
          Projects
        </div>
        <div
          class="cursor-pointer hover:text-primary"
          @click="$emit('scroll-to', 'contact')"
        >
          Contact
        </div>
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
          @click="$emit('handle-menu', !props.isMenuOpen)"
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
        class="absolute h-screen p-10 w-full z-10 top-[4.5rem] left-0 bg-white dark:bg-mirage-950"
      >
        <ul>
          <li
            class="py-2 cursor-pointer hover:text-primary"
            @click="$emit('scroll-to', 'home', props.isMenuOpen)"
          >
            Home
          </li>
          <li
            class="py-2 cursor-pointer hover:text-primary"
            @click="$emit('scroll-to', 'skills', props.isMenuOpen)"
          >
            Skills
          </li>
          <li
            class="py-2 cursor-pointer hover:text-primary"
            @click="$emit('scroll-to', 'projects', props.isMenuOpen)"
          >
            Projects
          </li>
          <li
            class="py-2 cursor-pointer hover:text-primary"
            @click="$emit('scroll-to', 'contact', props.isMenuOpen)"
          >
            Contact
          </li>
        </ul>
      </div>
    </UContainer>
  </nav>
</template>

<script setup lang="ts">
definePageMeta({
  colorMode: 'light',
});

const props = defineProps<{
  isMenuOpen: boolean;
}>();

const emit = defineEmits(['scroll-to', 'handle-menu']);

const isDarkMode = ref(false);
const windowWidth = ref(window?.innerWidth);
const colorMode = useColorMode();

watch(windowWidth, (newWindowWidth) => {
  if (newWindowWidth > 768) {
    emit('handle-menu', false);
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
