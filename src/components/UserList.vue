<template>
    <li class= "user_list" v-for="user in users">
        <div class="class_container">
            <UserCard :user="user"/>
        </div>
    </li>

</template>

<script setup>
import UserCard from './UserCard.vue'
import { ref } from 'vue'

let id = 1;

const users = ref(
    [
        {id: id++, firstName: 'Neymar', lastName:'Pai', email: 'akira.takiroto@gmail.com', profilePictureURL:'https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcSlzmYCFHcgQbTEpYyMa7EnLQPoO_RB_qCrNw&s', supportURL:'', funcao: 'Desenvolvedor'},
        {id: id++, firstName: 'Neymar', lastName:'Jr', email: 'najila@gmail.com', profilePictureURL:'https://bid.cbf.com.br/foto-atleta/292791', supportURL:'', funcao: 'Perninha'},
        {id: id++, firstName: 'Frank', lastName:'Ocean', email: 'nikes@gmail.com', profilePictureURL:'https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcT3y9MhlHjC9ml5Ze-SzfgZ_NCpOSR9F25lDw&s', supportURL:'', funcao: 'Joalheiro'},
    ]
) 

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