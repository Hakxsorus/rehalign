<script setup lang="ts">
import { useButtonGroup } from '@nuxt/ui/runtime/composables/useButtonGroup.js';
import { RouterLink, RouterView } from 'vue-router'
import 'leaflet/dist/leaflet.css'

const items = [
  { label: 'Home', icon: 'i-lucide-house', to: '/' },
  { label: 'Services', icon: 'i-lucide-briefcase', to: '/services' },
  { label: 'Locations', icon: 'i-lucide-map-pin', to: '/location' },
  { label: 'Contact', icon: 'i-lucide-mail', to: '/contact' },
  { label: 'About', icon: 'i-lucide-mail', to: '/about' }
]
</script>

<template>
  <UApp>
    <UHeader class="bg-gray-100">
      <template #title>
        <div class="flex items-center space-x-2">
          <img src="./assets/Logo-NoText.png" alt="Rehaligned" class="h-10 w-auto" />
          <h1 class="text-xl font-semibold mt-1">
            <span class="text-[#37474f]">Reh</span>
            <span class="text-[#aeea00]">align</span>
          </h1>
        </div>
      </template>
      <UNavigationMenu :items="items" />
      <template #right>
        <UButton icon="i-lucide-book-check" variant="subtle">Free Online Assessment</UButton>
      </template>
      <template #body>
        <UNavigationMenu :items="items" orientation="vertical" class="-mx-2.5" />
      </template>
    </UHeader>
    <RouterView />
  </UApp>
</template>




<!-- <template>
  <header>
    <img alt="Vue logo" class="logo" src="@/assets/logo.svg" width="125" height="125" />

    <div class="wrapper">
      <HelloWorld msg="You did it!" />

      <nav>
        <RouterLink to="/">Home</RouterLink>
        <RouterLink to="/about">About</RouterLink>
      </nav>
    </div>
  </header>

  <RouterView />
</template> -->
