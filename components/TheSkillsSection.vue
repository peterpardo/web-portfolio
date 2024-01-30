<template>
  <div
    ref="skillsRef"
    class="bg-mirage-950 text-white min-h-[110vh] px-10 py-40 grid place-content-center w-full"
  >
    <div
      class="flex flex-col md:flex-row md:justify-between w-full gap-10"
      v-motion-slide-visible-left
    >
      <div class="flex flex-col flex-1 justify-start gap-y-5">
        <h1 class="font-semibold text-6xl">
          My
          <span class="text-primary">Skills</span>
        </h1>
        <p>Here is the list of the technologies I learned:</p>
        <div class="flex justify-between">
          <ul class="list-disc list-inside flex-1">
            <li class="py-2">HTML</li>
            <li class="py-2">CSS</li>
            <li class="py-2">Javscript</li>
            <li class="py-2">Vuejs</li>
            <li class="py-2">Reactjs</li>
            <li class="py-2">Nodejs</li>
            <li class="py-2">Php</li>
            <li class="py-2">Laravel</li>
            <li class="py-2">MySQL</li>
          </ul>
          <ul class="list-disc list-inside flex-1">
            <li class="py-2">
              Docker -
              <span class="text-gray-400"
                >This one is challenging to learn but really helpful in
                development</span
              >
            </li>
            <li class="py-2">
              AWS -
              <span class="text-gray-400">
                Experienced deploying projects here using "EC2 Instances"
              </span>
            </li>
            <li class="py-2">
              DigitalOcean -
              <span class="text-gray-400"
                >Also experienced deploying projects here using "Droplets"</span
              >
            </li>
          </ul>
        </div>
      </div>
      <div class="grid grid-cols-4 gap-y-5 flex-1">
        <div
          v-for="icon in devIcons"
          class="grid place-items-center mx-auto border border-white w-16 h-16 rounded-md md:w-20 md:h-20"
        >
          <UIcon :name="icon" class="w-10 h-10 md:w-14 md:h-14" dynamic />
        </div>
      </div>
    </div>
  </div>
</template>

<script setup lang="ts">
const skillsRef = ref<HTMLElement | null>(null);

defineExpose({
  skillsRef,
});

const devIcons = [
  "i-devicon-react",
  "i-devicon-vuejs",
  "i-devicon-nuxtjs",
  "i-devicon-javascript",
  "i-devicon-css3-wordmark",
  "i-devicon-php",
  "i-devicon-html5",
  "i-devicon-laravel",
  "i-devicon-amazonwebservices-wordmark",
  "i-devicon-digitalocean-wordmark",
  "i-devicon-nodejs-wordmark",
  "i-devicon-mysql-wordmark",
  "i-devicon-docker-wordmark",
];
</script>
