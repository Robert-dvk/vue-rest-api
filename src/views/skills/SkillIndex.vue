<script setup>
    import useSkills from '@/composables/skills.js';
    import { onMounted } from 'vue';

    const { skills, getSkills, destroySkill } = useSkills();

    onMounted(() => getSkills());
    
</script>
<template>
    <div class="mt-24">
        <div class="flex justify-end p-2 m-2">
            <RouterLink :to="{name: 'SkillCreate' }" class="px-4 py-2 mr-4 bg-indigo-500 hover:bg-indigo-800 rounded text-white">New Skill</RouterLink>
        </div>
        <div class="relative overflow-x-auto">
            <table class="w-full text-sm text-left rtl:text-right text-gray-500 dark:text-gray-400">
                <thead class="text-xs text-gray-700 uppercase bg-gray-50 dark:bg-gray-700 dark:text-gray-400">
                    <tr>
                        <th scope="col" class="px-6 py-3">
                            Name
                        </th>
                        <th scope="col" class="px-6 py-3">
                            Slug
                        </th>
                        <th scope="col" class="px-6 py-3">
                            Actions
                        </th>
                    </tr>
                </thead>
                <tbody>
                    <tr v-for="(skill, index) in skills" :key="index" class="bg-white border-b dark:bg-gray-800 dark:border-gray-700">
                        <td class="px-6 py-3">{{ skill.name }}</td>
                        <td class="px-6 py-3">{{ skill.slug }}</td>
                        <td class="px-6 py-3">
                            <RouterLink :to="{name: 'SkillEdit', params: {id: skill.id}}" class="px-4 py-2 bg-green-500 hover:bg-green-800 rounded text-white mr-2">Update</RouterLink>
                            <button @click="destroySkill(skill.id)" class="px-4 py-2 mr-4 bg-red-600 hover:bg-red-800 rounded text-white">Delete</button>
                        </td>
                    </tr> 
                </tbody>
            </table>
        </div>
    </div>
</template>