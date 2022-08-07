<template>
  <div class="container">
    <h1 class="title">Free Fuel Pass</h1>
    <QuotaView :eligible-quota="eligibleQuota" :used-quota="usedQuota"></QuotaView>
    <FillMeUp @click-fill="handleOnClickFill" :disabled="isDisabledFill"></FillMeUp>
  </div>
</template>

<script setup>
import { onMounted, ref } from 'vue'
import FillMeUp from './components/FillMeUp.vue'
import QuotaView from './components/QuotaView.vue'

const eligibleQuota = ref(0)
const usedQuota = ref(0)
const isDisabledFill = ref(false)

const handleOnClickFill = ({ amount }) => {
  if (usedQuota.value >= eligibleQuota.value) return isDisabledFill.value = true
  usedQuota.value += amount
}

onMounted(() => {
  eligibleQuota.value = Math.floor(Math.random() * 20) + 5
})
</script>

<style scoped>
.container {
  display: flex;
  flex-direction: column;
  padding: 50px 100px;
}

.title {
  text-align: center;
}
</style>