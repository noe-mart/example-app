
<script setup>
import AuthenticatedLayout from "@/Layouts/AuthenticatedLayout.vue"
import { Head } from '@inertiajs/vue3'
import NavLink from '@/Components/NavLink.vue'
import DropdownLink from '@/Components/DropdownLink.vue'
import { ref } from "vue"
import Post from "@/Components/Post.vue"

const props = defineProps(['posts'])

const isEditOpen = ref(false)


</script>

<template>
    <Head title="Post"></Head>

    <AuthenticatedLayout>
        <div class="max-w-2xl mx-auto p-4 sm:p-6 lg:p-8">
            <h1>Posts</h1>

            <div>
                <ul>
                    <li v-for="(post, index) in props.posts" class="flex justify-between mt-2 border-b-2 border-black-400" :key="post.id">
                        <div class="">
                            {{ index + 1 }}
                            <NavLink class="text-black" :href="route('posts.show', post)">
                                {{ post.title }}
                            </NavLink>
                            <p>
                                <NavLink :href="route('users.show', post.user)">
                                    <span v-if="post.user.id === $page.props.auth.user.id">By me</span>
                                    <span v-else>By {{ post.user.name }}</span>
                                </NavLink>
                            </p>

                        </div>
                        <div v-if="$page.props.auth.user.id === post.user.id" class="relative inline-block">
                            
                            <Post :post="post"/>
                        </div>
                    </li>
                </ul>
            </div>

        </div>

    </AuthenticatedLayout>
</template>