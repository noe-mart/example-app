<script setup>
import { Head } from '@inertiajs/vue3'
import AuthenticatedLayout from '@/Layouts/AuthenticatedLayout.vue'

const props = defineProps(['post'])

</script>

<template>
    <Head title="Post"></Head>

    <AuthenticatedLayout>
        <div class="max-w-2xl mx-auto p-4 sm:p-6 lg:p-8">
            <h1 style="font-size: large;">{{ post.title }}</h1>
            <p><span>{{ post.user.name }}</span></p>
            <div style="margin-top: 20px;">
                {{ post.body }}
            </div>
        </div>

    </AuthenticatedLayout>
</template>