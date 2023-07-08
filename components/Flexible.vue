<script setup>
const props = defineProps({
    layout: Object
})
</script>

<template>
    <div v-if="layout.acf_fc_layout == 'header'">
        <Header :layout="layout" />
    </div>

    <div v-if="layout.acf_fc_layout == 'cta'">
        <Cta :layout="layout" />
    </div>
</template>