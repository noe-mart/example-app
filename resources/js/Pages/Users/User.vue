<script setup>
import AuthenticatedLayout from '@/Layouts/AuthenticatedLayout.vue';
import { Head } from '@inertiajs/vue3';
import NavLink from '@/Components/NavLink.vue';

const props = defineProps(['user'])

// console.log(props)
</script>

<template>
    <Head title="Usuario"></Head>

    <AuthenticatedLayout>
        <div class="max-w-2xl mx-auto p-4 sm:p-6 lg:p-8">

            <h1 class=""> Post de {{ user.name }}</h1>
            <!-- 
                                <pre>
                                    {{ user.posts }}
                                </pre> -->


            <ul class="mt-4">
                <li class="mt-2" v-for="post in props.user.posts">
                    <NavLink :href="route('posts.show', post)">
                        {{ post.title }}
                    </NavLink>
                </li>
            </ul>
        </div>

    </AuthenticatedLayout>
</template>
