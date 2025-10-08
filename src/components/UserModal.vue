<template>
    <div class="modal">
        <div class="modal-content">
            <h1>{{ user.name }}</h1>
            <p>EMAIL: {{ user.email }}</p>
            <p>USER NAME: {{ user.username }}</p>
            <p>ADDRESS: {{ user.address.street }}, {{ user.address.city }}</p>
            <p>ID: {{user.id  }}</p>
            <p>PHONE: {{ user.phone }}</p>
            <p>COMPANY: {{ user.company.name }}</p>
            <button @click="$emit('modalFalse')">Close</button>
        </div>

    </div>
</template>
<script setup>
import { defineProps, ref } from "vue";

const props = defineProps({
    prop_userSelected: Object,
})
const user = ref(props.prop_userSelected);
</script>

<style>
.modal {
    position: fixed;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    background-color: rgba(0, 0, 0, 0.5);
    display: flex;
    justify-content: center;
    align-items: center;
}

.modal-content {
    background-color: white;
    width: 400px;
    border-radius: 10px;
    padding: 20px;
}
</style>