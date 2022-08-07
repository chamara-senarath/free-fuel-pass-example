<template>
    <div>
        <h1>Eligible Weekly Quota: {{ eligibleQuota }} L</h1>
        <h1>Balance Weekly Quota: {{ balanceQuota }} L</h1>
    </div>
</template>

<script setup>
import { computed } from 'vue';

const props = defineProps({
    eligibleQuota: {
        type: Number,
        default: 0,
    },
    usedQuota: {
        type: Number,
        default: 0,
    }
})
const balanceQuota = computed(() => props.eligibleQuota - props.usedQuota)
</script>