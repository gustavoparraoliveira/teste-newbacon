<template>
    <div class="container">
        <header>
            <span>
                <h1>#{{ routeId }}</h1>
            </span>
            <div class="back_button_container">
                <RouterLink to='/' style="text-decoration:none"><button>Voltar</button></RouterLink>
            </div>
        </header>
        <div class = "avatar_name_container">
            <div>
                <img :src=user.avatar>
            </div>
            <div class = "name_container">
                <div>
                    <label>Primeiro nome</label>
                </div> 
                <div>
                    <span>{{ user.first_name }}</span>
                </div>
            </div>
            <div class = "name_container">
                <div>
                    <label>Último nome</label>
                </div> 
                <div>
                    <span>{{ user.last_name }}</span>
                </div>
            </div>
        </div>
        <div class = "description_container">
            <div>
                <label>Endereço de e-mail</label>
            </div> 
            <div>
                <span>{{ user.email }}</span>
            </div>
        </div>
        <div class = "description_container">
            <div>
                <label>Link do avatar</label>
            </div> 
            <div>
                <span>{{ user.avatar }}</span>
            </div>
        </div>
        <div class = "description_container">
            <div>
                <label>Link de suporte</label>
            </div> 
            <div>
                <span>{{ support.url }}</span>
            </div>
        </div>
        <div class = "description_container">
            <div>
                <label>Descrição do usuário</label>
            </div> 
            <div>
                <span>{{ support.text }}</span>
            </div>
        </div>
    </div>
</template>

<script setup>

import { ref, onMounted  } from 'vue';
import { useRoute } from 'vue-router';
import UserCard from './UserCard.vue';

const user = ref([])
const support = ref ([])

const route = useRoute();
const routeId = route.params.id;

async function fetchData () {

    const response = await fetch('https://reqres.in/api/users/'+routeId);

    if (!response.ok) {
            console.log('failed')//throw new Error('Login failed');
    }
    else {
        const data = await response.json();

        user.value = data.data;
        support.value = data.support;

        console.log(data.data)
        console.log(data.support)
    }
}

onMounted(() => {
fetchData();
})

</script>

<style scoped>

* {
    border: none;

}

header {
    display: flex;
    max-width: 600px;
    width: 100%;
    justify-content: space-between;
    align-content: center;  
    align-items: center;
}
    
h1 {
    font-size: 48px;
    margin: 10px;
    align-content: center;
}

.back_button_container {
    background-color: #F7F7F7;
    width: 30%;
    height: 48px;
    text-align: center;
    align-content: center;
    border-radius: 5px;
    color: black;
    font-weight: 0;
}

.back_button_container button {
    width: 100%;
    height: 100%;
    color: black;
    text-decoration: none;
    font-weight: bold;
}

button, input, select {
    all:unset;
    font-size: 15px;
}

.container {
    margin: auto;
}

.img {
    width: 120px;
}

.avatar_name_container {
    width: 80%;
    display: flex;
    justify-content: space-between;
    padding: 15px;
    align-items: center;
}

.name_container {
    height: 60px;
    display: flex;
    flex-direction: column;
    align-items:stretch;
}

.description_container {
    width: 80%;
    height: 50px;
    padding: 15px;
    display: flex;
    flex-direction: column;
    align-items: stretch;
}

.description_container div {
    flex: 1;
}

.name_container div {
    flex: 1;
}


label {
    color: gray;
    font-size: 16px;
}

span {
    color: black;
    font-weight: 600;
    font-size: 18px;
}

</style>