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

const { data, pending, error, refresh } = await useFetch('http://nuxt3-headless/wp-json/wp/v2/pages', {
    query: { slug: slug.value }
})
</script>

<template>
    <div class="container mx-auto mt-8">
        <p v-if="route">
             {{ route }}
        </p>

        <div v-if="data">
            {{ data[0].title.rendered }}
        </div>

        <div v-if="slug" class="bg-blue-300 mt-8 text-2xl p-4">
            {{ slug }}
        </div>


    </div>
</template>