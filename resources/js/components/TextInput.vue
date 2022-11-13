<script setup>
import { onMounted, ref } from "vue";

defineProps(["modelValue"]);

defineEmits(["update:modelValue"]);

const input = ref(null);
</script>

<template>
    <input
        class=""
        :value="modelValue"
        @input="$emit('update:modelValue', $event.target.value)"
        ref="input"
    />
</template>
