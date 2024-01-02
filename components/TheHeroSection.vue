<template>
  <div ref="homeRef" class="h-[95vh] px-10 grid place-content-center">
    <div class="flex flex-col items-center justify-center gap-y-10">
      <h1 class="text-6xl text-center font-bold md:text-7xl">
        <span class="text-primary">Peter</span> Pardo
      </h1>
      <p
        class="max-w-[700px] text-gray-400 text-center text-sm leading-loose md:text-md"
      >
        I'm a full-stack web developer. I love to start projects but most of
        them are not finished. In my spare time, I browse facebook, instagram,
        and youtube. I do workout to maintain my health and sometimes I look out
        for new trending technologies in the programming world.
      </p>
      <div class="w-full flex items-center justify-center gap-x-5">
        <UButton color="gray" @click="$emit('scroll-to', 'contact')">
          <UIcon name="i-ic-baseline-waving-hand" dynamic />
          Say Hello!
        </UButton>
        <UButton @click="$emit('scroll-to', 'projects')">
          <UIcon name="i-ic-baseline-rocket-launch" dynamic />
          See my works
        </UButton>
      </div>
    </div>
  </div>
</template>

<script setup lang="ts">
const homeRef = ref<HTMLElement | null>(null);

defineExpose({
  homeRef,
});

defineEmits(['scroll-to']);
</script>
