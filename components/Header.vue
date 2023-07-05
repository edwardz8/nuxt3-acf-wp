<script setup>
const props = defineProps({
    layout: Object 
})

</script>

<template>
    <ClientOnly>
        <div>
            <h2>{{ layout?.title }}</h2>
            <p>{{ layout?.subtitle }}</p>
        </div>
    </ClientOnly>
</template>