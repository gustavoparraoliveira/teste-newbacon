<template>
    <li class= "user_list" v-for="user in users">
        <div class="class_container">
            <UserCard :user="user"/>
        </div>
    </li>

</template>

<script setup>
import UserCard from './UserCard.vue'
import { onMounted, ref } from 'vue'

let id = 1;

const users = ref([])
console.log(users.value);

const usersDefault = [
        {id: id++, first_name: 'Neymar', last_name:'Pai', email: 'akira.takiroto@gmail.com', avatar:'https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcSlzmYCFHcgQbTEpYyMa7EnLQPoO_RB_qCrNw&s', supportURL:'', funcao: 'Desenvolvedor'},
        {id: id++, first_name: 'Neymar', last_name:'Jr', email: 'najila@gmail.com', avatar:'https://bid.cbf.com.br/foto-atleta/292791', supportURL:'', funcao: 'Perninha'},
        {id: id++, first_name: 'Frank', last_name:'Ocean', email: 'nikes@gmail.com', avatar:'https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcT3y9MhlHjC9ml5Ze-SzfgZ_NCpOSR9F25lDw&s', supportURL:'', funcao: 'Joalheiro'},
    ]

async function fetchData () {

    const response = await fetch('https://reqres.in/api/users?page=1');

    if (!response.ok) {
            throw new Error('Fetch failed')
    }
    else {
        const data = await response.json();
        users.value = data.data;
        console.log('data fetched')
    }
}

onMounted(() => { fetchData() })

</script>

<style scoped>

.user_list {
    list-style: none;
}

.class_container {
    margin: 15px 0px 15px 0px;
    display: flex;
    flex:1;
}

</style>