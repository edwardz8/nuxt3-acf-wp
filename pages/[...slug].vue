<script setup>
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

const { data, pending, error, refresh } = await useLazyFetch(
    'https://nuxt3-headless.flywheelsites.com/wp-json/wp/v2/pages', {
    query: { slug: slug.value }
})
</script>

<template>
    <ClientOnly>
        <div class="container mx-auto mt-8">
            <div>
                <Header :title="data[0].title.rendered" :subtitle="data[0].content.rendered" />
            </div>
            
            <div v-for="layout in data[0].acf.flexible">
                <Flexible :layout="layout" />
            </div>
            
            <div class="mt-8">{{ route }}</div>
        </div>
    </ClientOnly>
</template>