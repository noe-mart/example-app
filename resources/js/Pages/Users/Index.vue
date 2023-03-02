<script setup>
import NavLink from '@/Components/NavLink.vue';
import AuthenticatedLayout from '@/Layouts/AuthenticatedLayout.vue';
import { Head } from '@inertiajs/vue3';


defineProps(['users'])

</script>

<template>
    <Head title="Usuarios"></Head>

    <AuthenticatedLayout>
        <div class="max-w-2xl mx-auto p-4 sm:p-6 lg:p-8">

            <h1>Usuarios</h1>

            <div>
                <ul>
                    <li v-for="user in users">
                        <NavLink :href="route('users.show', user)">
                            {{ user.name }}
                        </NavLink>
                    </li>
                </ul>
            </div>


        </div>

    </AuthenticatedLayout>
</template>