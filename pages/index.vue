<template>
  <div
    class="dark:dark:bg-mirage-950"
    :ui="{
      padding: 'px-0 sm:px-0 lg:px-8',
    }"
  >
    <TheNavbar
      @scroll-to="scrollTo"
      :is-menu-open="isMenuOpen"
      @handle-menu="handleMenu"
    />
    <TheHeroSection ref="homeRef" />
    <TheSkillsSection ref="skillsRef" />
    <TheProjectsSection ref="projectsRef" />
    <TheContactSection ref="contactRef" />
  </div>
</template>

<script setup lang="ts">
const homeRef = ref(null);
const skillsRef = ref(null);
const projectsRef = ref(null);
const contactRef = ref(null);
const isMenuOpen = ref(false);

function handleMenu(value: boolean) {
  isMenuOpen.value = value;
}

function scrollTo(view: string, isOpen?: boolean) {
  if (isOpen) {
    isMenuOpen.value = false;
  }

  if (view === 'home') {
    window.scrollTo({ top: 0, behavior: 'smooth' });
  } else if (view === 'skills') {
    skillsRef.value?.skillsRef.scrollIntoView({
      behavior: 'smooth',
      block: 'start',
    });
  } else if (view === 'projects') {
    projectsRef.value?.projectsRef.scrollIntoView({
      behavior: 'smooth',
      block: 'start',
    });
  } else if (view === 'contact') {
    contactRef.value?.contactRef.scrollIntoView({
      behavior: 'smooth',
      block: 'start',
    });
  }
}
</script>
