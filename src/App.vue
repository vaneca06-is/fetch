<template>
  <div>
    <h1>USUARIOS</h1>
    <UserTable :userTable="users" @show-details="openModal"></UserTable>
    <UserModal v-if="showModal" :prop_userSelected="selectedUser" @modalFalse="setModalFalse"> </UserModal>
  </div>
</template>

<script setup>
import { ref, onMounted } from 'vue';
import UserTable from "./components/UserTable.vue"
import UserModal from './components/UserModal.vue';

const users = ref([]); //se inicializa con un arreglo vacio
const selectedUser = ref({});
const showModal = ref(false)

onMounted(async () => {
  try {
    const res = await fetch("https://jsonplaceholder.typicode.com/users");

    users.value = await res.json();
    console.log('users', users.value)
  } catch (error) {
    console.error("Ha ocurrido un error al cargar los datos", error);
  }
})

const openModal = (user) => {
  console.log(user);
  selectedUser.value = user
  showModal.value = true
};

const setModalFalse = () => {
  showModal.value = false
}
</script>