<script setup>
const props = defineProps({
    layout: Object
})
</script>

<template>
        <h2>{{ layout.headline }}</h2>
        <!--     <a :href="layout.link_1.url" class="mt-6 text-lg">{{ layout.link_1.title }}</a>  -->
</template>