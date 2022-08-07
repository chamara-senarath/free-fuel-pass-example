<template>
    <button class="fill-me-button" @click="handleOnClickFill">Fill Me Up (1L)</button>
</template>

<script setup>
import { computed } from 'vue'
const props = defineProps({
    disabled: {
        type: Boolean,
        default: false
    }
})
const emit = defineEmits(['click-fill'])

const handleOnClickFill = () => {
    emit('click-fill', { amount: 1 })
}

const buttonCursor = computed(() => props.disabled ? 'not-allowed' : 'pointer')
</script>

<style scope>
.fill-me-button {
    background-color: initial;
    background-image: linear-gradient(-180deg, #FF7E31, #E62C03);
    border-radius: 6px;
    border-color: white;
    box-shadow: rgba(0, 0, 0, 0.1) 0 2px 4px;
    color: #FFFFFF;
    transition: box-shadow .2s;
    height: 50px;
    cursor: v-bind('buttonCursor');
    font-size: 16px;
}

.fill-me-button:hover {
    box-shadow: rgba(253, 76, 0, 0.5) 0 3px 8px;
}
</style>