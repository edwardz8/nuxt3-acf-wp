<script setup lang="ts">
const route = useRoute()
const slug = ref('')

if (route.params.slug) {
    let lastIndex = route.params.slug.length - 1
    if (!route.params.slug[lastIndex]) {
        slug.value = route.params.slug[lastIndex - 1]
    } else {
        slug.value = route.params.slug[lastIndex]
    }
} else {
    slug.value = 'home'
}

const { data, pending, error, refresh } = await useLazyFetch('https://nuxt3-headless.flywheelsites.com/wp-json/wp/v2/pages', {
    query: { slug: slug.value }
})
</script>

<template>
    <div class="container mx-auto mt-8">
        <div>
            {{ data }}
        </div>

        <div class="bg-blue-300 mt-8 text-2xl p-4">
            {{ slug }}
        </div>

        <div class="mt-8">{{ route }}</div>


    </div>
</template>