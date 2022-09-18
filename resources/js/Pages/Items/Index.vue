<script setup>
import AuthenticatedLayout from '@/Layouts/AuthenticatedLayout.vue';
import InputError from '@/Components/InputError.vue';
import PrimaryButton from '@/Components/PrimaryButton.vue';
import { useForm, Head} from '@inertiajs/inertia-vue3';

const form = useForm({
    message: '',
    itemName: '',
});

</script>

<template>
    <Head title="Items" />
 
    <AuthenticatedLayout>
        <template #header>
            <h2 class="font-semibold text-xl text-gray-800 leading-tight">
                Items
            </h2>
        </template>

        <div class="py-12">
            <div class="max-w-7xl mx-auto sm:px-6 lg:px-8">
                <div class="bg-white overflow-hidden shadow-sm sm:rounded-lg">
                    <div class="p-6 bg-white border-b border-gray-200">
                        <div class="max-w-2xl mx-auto p-4 sm:p-6 lg:p-8">
                            <form @submit.prevent="form.post(route('items.store'), { onSuccess: () => form.reset() })">
                                <textarea
                                    v-model="form.message"
                                    placeholder="What's on your mind?"
                                    class="block w-full border-gray-300 focus:border-indigo-300 focus:ring focus:ring-indigo-200 focus:ring-opacity-50 rounded-md shadow-sm"
                                ></textarea>
                                {{form.message}}
                                <input 
                                    v-model="form.itemName"
                                    class="block w-full border-gray-300 focus:border-indigo-300 focus:ring focus:ring-indigo-200 focus:ring-opacity-50 rounded-md shadow-sm"
                                type="text">
                                {{form.itemName}}
                                <InputError :message="form.errors.message" class="mt-2" />
                                <PrimaryButton class="mt-4">Items</PrimaryButton>
                            </form>
                        </div>
                    </div>
                </div>
            </div>
        </div>

        
    </AuthenticatedLayout>
</template>