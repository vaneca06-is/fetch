<template>
    <table>
        <thead>
            <tr>
                <th>ID</th>
                <th>Npmbre</th>
                <th>Email</th>
                <th>Acciones</th>
            </tr>
        </thead>
        <tbody>
            <tr v-for="user in props.userTable" :key="user.id">
                <td>{{ user.id }}</td>
                <td>{{ user.name }}</td>
                <td>{{ user.email }}</td>
                <td>
                    <button @click="$emit('show-details', user)">Ver</button>
                </td>
            </tr>
        </tbody>
    </table>
</template>

<script setup>
import { defineProps } from "vue";

const props = defineProps({
    userTable: Array,
})

//const emit = defineEmits(["show-details"]); // SAME TO USE "$emit('show-details', user)
</script>
