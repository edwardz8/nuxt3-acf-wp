<script setup>
const props = defineProps({
    title: String,
    subtitle: String
})

</script>

<template>
    <div>
        <div>
            <h2>{{ title }}</h2>
            <p>{{ subtitle }}</p>
        </div>
    </div>
</template>