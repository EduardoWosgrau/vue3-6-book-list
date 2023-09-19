<script setup>

import { computed } from 'vue';

const props = defineProps(['courses']);

const coursesDone = computed(() => {
    return props.courses.filter(course => course.done)
});

</script>

<template>
    <div>{{ `${coursesDone.length } completed courses of ${courses.length} total` }}</div>

</template>