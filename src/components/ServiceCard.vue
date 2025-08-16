<!-- components/RehalignCard.vue -->
<template>
    <UCard :variant="variant" :ui="ui">
        <!-- Header: Image with "New" badge -->
        <template #header>
            <div class="relative">
                <img :src="imgSrc" :alt="imgAlt || title" class="h-40 w-full object-cover" />
                <UBadge v-if="isNew" color="primary" variant="solid" class="absolute top-2 right-2">
                    New
                </UBadge>
            </div>
        </template>

        <!-- Body: Title + Subtitle -->
        <div>
            <h3 class="text-base font-semibold leading-tight">{{ title }}</h3>
            <p v-if="subtitle" class="mt-1 text-sm text-muted-foreground">
                {{ subtitle }}
            </p>
        </div>

        <!-- Footer (optional slot passthrough) -->
        <template #footer>
            <slot name="footer" />
        </template>
    </UCard>
</template>

<script setup lang="ts">
defineProps<{
    title: string
    subtitle?: string
    imgSrc: string
    imgAlt?: string
    isNew?: boolean
    variant?: 'solid' | 'outline' | 'soft' | 'subtle'
    ui?: {
        root?: any
        header?: any
        body?: any
        footer?: any
    }
}>()
</script>
