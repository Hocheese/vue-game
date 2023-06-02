<template>
    <div>{{ data }}</div>
</template>
<script setup>
import { ref, onMounted } from 'vue';

const data = ref('当前时间')

onMounted(() => {
    setInterval(() => {
        data.value = '当前时间:'+(new Date())
    }, 1000)
})
</script>