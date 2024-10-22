<template>
    <div class="container">
        <header>
            <span>
                <h1>#{{ routeId }}</h1>
            </span>
            <div class="back_button_container">
                <RouterLink to='/' style="text-decoration:none"><button class="back_button">Voltar</button></RouterLink>
            </div>
        </header>
        <div class = "avatar_firstname_lastname_container">
            <div>
                <img :src=user.avatar>
            </div>
            <div class = "name_container">
                <div>
                    <label>Primeiro nome</label>
                </div> 
                <div class="input_field">
                    <input style="padding: 10px 0px 10px 10px;" :value="user.first_name"></input>
                </div>
            </div>
            <div class = "name_container">
                <div>
                    <label>Último nome</label>
                </div> 
                <div class="input_field">
                    <input style="padding: 10px 0px 10px 10px;" :value="user.last_name"></input>
                </div>
            </div>
        </div>
        <div class = "details_container">
            <div>
                <label>Endereço de e-mail</label>
            </div> 
            <div class="input_field">
                <input style="width: 95%; padding: 10px 0px 10px 10px;" :value="user.email"></input>
            </div>
            <div>
                <label>Link do avatar</label>
            </div> 
            <div class="input_field">
                <input style="width: 95%; padding: 10px 0px 10px 10px;" :value="user.avatar"></input>
            </div>
            <div>
                <label>Link de suporte</label>
            </div> 
            <div class="input_field">
                <input style="width: 95%; padding: 10px 0px 10px 10px;" :value="support.url"></input>
            </div>
            <div>
                <label>Descrição do usuário</label>
            </div> 
            <div class="input_field">
                <input style="width: 95%; padding: 10px 0px 10px 10px;" :value="support.text"></input>
            </div>
        </div>
        <div class="save_user_button_container">
            <button style="color:white">Salvar dados do usuário</button>
        </div>
    </div>
</template>

<script setup>

import { ref, onMounted  } from 'vue';
import { useRoute } from 'vue-router';
import UserCard from './UserCard.vue';

const user = ref([])
const support = ref ([])

const route = useRoute()
const routeId = route.params.id

async function fetchData () {

    const response = await fetch('https://reqres.in/api/users/'+routeId)

    if (!response.ok) {
            console.log('Fetch falhou')
    }
    else {
        const data = await response.json()

        user.value = data.data
        support.value = data.support

        console.log(data.data)
        console.log(data.support)
        
    }
}

onMounted(() => {
        fetchData();
        console.log('data fetched')
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

.back_button {
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

.avatar_firstname_lastname_container {
    width: 80%;
    gap: 10px;
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

.details_container {
    width: 90%;
    height: 50px;
    padding: 15px;
    display: flex;
    flex-direction: column; 
    gap: 13px;
    height: 100%;
}

.details_container div {
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

.input_field {
    box-sizing: border-box;
    background-color: rgb(255, 255, 255);
    height: 40px;
    width: 100%;
    border-radius: 5px;
    border-width: 1px;
    border-color: rgb(192, 192, 192);
    border-style: solid;
    padding: 2px;
}

.input_field_value {
    width: 100%;
}

.save_user_button_container {
    display: inline-block;
    background-color: black;
    width: 100%;
    height: 48px;
    text-align: center;
    align-content: center;
    border-radius: 5px;
    margin-top: 15px;
    position: relative;
}


</style>