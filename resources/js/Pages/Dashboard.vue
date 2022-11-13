<script setup>
import AuthenticatedLayout from "@/Layouts/AuthenticatedLayout.vue";
import PrimaryButton from "@/Components/PrimaryButton.vue";
import { Head } from "@inertiajs/inertia-vue3";
import { computed, onMounted, onUnmounted, ref } from "vue";

const open = ref(false);
</script>

<template>
    <Head title="Dashboard" />

    <AuthenticatedLayout>
        <template #header>
            <h2 class="font-semibold text-xl text-gray-800 leading-tight">
                Dashboard
            </h2>
        </template>

        <div class="py-12">
            <div class="max-w-7xl mx-auto sm:px-6 lg:px-8">
                <div
                    class="flex flex-col bg-white overflow-hidden shadow-sm sm:rounded-lg"
                >
                    <div class="p-6 bg-white border-b border-gray-200">
                        <primary-button :type="submit" @click="open = !open">
                            Button
                        </primary-button>

                        <div v-if="open">Hide</div>
                    </div>
                </div>
            </div>
        </div>
    </AuthenticatedLayout>
</template>
