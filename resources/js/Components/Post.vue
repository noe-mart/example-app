<script setup>
import { ref } from 'vue';
import Modal from '@/Components/Modal.vue';
import PostForm from '@/Components/PostForm.vue';

const props = defineProps(['post'])

const isModalOpen = ref(false)
const isEditing = ref(false)

const closeModal = () => {
    isEditing.value = false
    isModalOpen.value = false
}
</script>

<template>
    <button @click="isModalOpen = !isModalOpen" class="p-4 border-indigo-200 border-1">
        <svg class="w-5 h-5 text-gray-800 dark:text-white" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 20 20"
            fill="currentColor">
            <path fill-rule="evenodd"
                d="M5.293 7.293a1 1 0 011.414 0L10 10.586l3.293-3.293a1 1 0 111.414 1.414l-4 4a1 1 0 01-1.414 0l-4-4a1 1 0 010-1.414z"
                clip-rule="evenodd" />
        </svg>
    </button>

    <div v-if="isModalOpen" class="absolute right-0 z-20 w-48 py-2 mt-2 origin-top-right bg-white rounded-md shadow-xl
                                        dark:bg-gray-800">
        <button @click="isEditing = true"
            class="block px-4 py-3 text-sm text-gray-600 capitalize transition-colors duration-300 
                                                            transform dark:text-gray-300 hover:bg-gray-100 dark:hover:bg-gray-700 dark:hover:text-white">
            Editar
        </button>
        <button class="block px-4 py-3 text-sm text-gray-600 capitalize transition-colors duration-300 transform dark:text-gray-300 
                                                hover:bg-gray-100 dark:hover:bg-gray-700 dark:hover:text-white">
            Eliminar
        </button>
    </div>

    <Modal :show="isEditing" @close="closeModal" :max-width="'2xl'" >
       <PostForm :post="post" @closeEmit="closeModal"/>
    </Modal>
</template>