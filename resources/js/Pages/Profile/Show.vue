<script setup>
import AuthenticatedLayout from '@/Layouts/AuthenticatedLayout.vue';
import Heading from '@/Components/Heading.vue';
import Chirp from '@/Components/Chirp.vue';
import Pagination from '@/Components/Pagination.vue';
import { Head } from '@inertiajs/vue3';

defineProps(['user','chirps','following']);
</script>

<template>
    <Head :title="user.name" />

    <AuthenticatedLayout>
        <Heading :user="user" :following="following"/>
        <div class="max-w-2xl mx-auto p-4 sm:p-6 lg:p-8">
            <div class="mt-6 bg-white shadow-sm rounded-lg divide-y">
                <Chirp
                    v-for="chirp in chirps.data"
                    :key="chirp.id"
                    :chirp="chirp"
                />
            </div>
            <Pagination :nextUrl="chirps.next_page_url" :prevUrl="chirps.prev_page_url"/>
        </div>
    </AuthenticatedLayout>
</template>
