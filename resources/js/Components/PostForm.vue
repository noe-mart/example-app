<script setup>
import { useForm } from '@inertiajs/vue3';

const props = defineProps(['post'])


const form = useForm({
    title: props.post.title,
    slug: props.post.slug,
    body: props.post.body
})


const emit = defineEmits(['closeEmit'])

const emitClose = () => {
    emit('closeEmit')
}

</script>
<template>
    <form class="p-4" @submit.prevent="form.put(route('posts.update', post.id))">
        <div class="gap-6 mt-4 sm:grid-cols-2">
            <div>
                <label class="text-gray-700 dark:text-gray-200" for="titulo">Titulo</label>
                <input v-model="form.title"
                    id="titulo" type="text"
                    class="block w-full px-4 py-2 mt-2 text-gray-700 bg-white border border-gray-200 rounded-md dark:bg-gray-800 dark:text-gray-300 dark:border-gray-600 focus:border-blue-400 focus:ring-blue-300 focus:ring-opacity-40 dark:focus:border-blue-300 focus:outline-none focus:ring">
            </div>

            <div>
                <label class="text-gray-700 dark:text-gray-200" for="slug">Slug</label>
                <input v-model="form.slug" 
                    id="slug" type="text"
                    class="block w-full px-4 py-2 mt-2 text-gray-700 bg-white border border-gray-200 rounded-md dark:bg-gray-800 dark:text-gray-300 dark:border-gray-600 focus:border-blue-400 focus:ring-blue-300 focus:ring-opacity-40 dark:focus:border-blue-300 focus:outline-none focus:ring">
            </div>

            <div>
                <label class="text-gray-700 dark:text-gray-200" for="body">Password Confirmation</label>
                <textarea v-model="form.body" 
                    id="body" type="password"
                    rows="10"
                    class="min-h-max block w-full px-4 py-2 mt-2 text-gray-700 bg-white border border-gray-200 rounded-md dark:bg-gray-800 dark:text-gray-300 dark:border-gray-600 focus:border-blue-400 focus:ring-blue-300 focus:ring-opacity-40 dark:focus:border-blue-300 focus:outline-none focus:ring">
                                </textarea>
            </div>
        </div>

        <div class="flex justify-end mt-6">
            <button @click="emitClose"
                class="px-8 py-2.5 leading-5 text-white transition-colors duration-300 transform bg-red-700 rounded-md hover:bg-red-600 focus:outline-none focus:bg-red-600">Cancelar</button>
            <button
                class="px-8 py-2.5 leading-5 text-white transition-colors duration-300 transform bg-gray-700 rounded-md hover:bg-gray-600 focus:outline-none focus:bg-gray-600">Guardar</button>

        </div>
    </form>
</template>


