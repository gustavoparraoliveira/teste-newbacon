<template>
    <div class="container">
        <header class="header">
            <label>
                <h1>Usuários</h1>
            </label>
            <div :class="new_user_button_toggle_class" @click="showNewUser= !showNewUser; handleFormState()">
                <button>{{ new_user_button_toggle_value }}</button>
            </div>
        </header>
        <Transition>
            <div v-if="showNewUser" class="form_container" id="form_container">
                <label>
                    <strong>Nome do usuário</strong>
                </label>
                <div>
                    <input id="name_input">
                </div>
                <label>
                    <strong>Função do usuário</strong>
                </label>
                <div class="dropdown">
                    <div class="select_container" id="select_container" @click.stop="toggleSelectOptions">
                        <div id="select_value" class ="select_value">
                            Selecione a função 
                        </div>
                        <div class="custom_arrow">
                            <img src="..\assets\caret-down-solid.svg"/>
                        </div>
                    </div>
                    <div class="select_options_container" id="select_options_container">
                        <ul>
                            <li @click.stop="populateSelectedValue('Desenvolvedor')">Desenvolvedor</li>
                            <li @click.stop="populateSelectedValue('Gerente de Projetos')">Gerente de Projetos</li>
                            <li @click.stop="populateSelectedValue('Tech Lead')">Tech Lead</li>
                            <li @click.stop="populateSelectedValue('UI/UX Designer')">UI/UX Designer</li>
                        </ul>
                    </div>
                </div>
                <div class="save_user_button_container">
                    <button style="color:white">Salvar dados do usuário</button>
                </div>
            </div>
        </Transition>
    </div>
</template>

<script setup>

import { ref } from 'vue';

let showNewUser = ref(false);

const new_user_button_toggle_class = ref("new_user_button_container")
const new_user_button_toggle_value = ref("Novo usuário")

function handleFormState () {
    if (showNewUser.value) {
        new_user_button_toggle_class.value = "cancel_button_container"
        new_user_button_toggle_value.value = "Cancelar"
    }
    else {
        new_user_button_toggle_class.value = "new_user_button_container"
        new_user_button_toggle_value.value = "Novo usuário"
    }
}

function toggleSelectOptions() {  
    document.getElementById("select_options_container").classList.toggle("show");
}

function populateSelectedValue(String) {
    document.getElementById("select_value").innerHTML = String;
    document.getElementById("select_value").style.color="black";
    document.getElementById("select_options_container").classList.toggle("show");
}

document.documentElement.addEventListener("click", function () {
  if (document.getElementById("select_options_container").classList.contains("show")) {
    toggleSelectOptions();
  }
});

</script>

<style scoped>

* {
    border: none;
}

.container {
    margin: 0px;
}

header {
    position: relative;
    display: flex;
    width: 592px;
    width: 100%;
    justify-content: space-between;
    align-content: center;  
    align-items: center;
    z-index: 2;
}

.header {
    background-color: white;
    margin: 0px;
    height: 120px;
}
    
h1 {
    font-size: 48px;
    margin: 10px;
    align-content: center;
}

.new_user_button_container {
    background-color: black;
    width: 30%;
    height: 48px;
    text-align: center;
    align-content: center;
    border-radius: 5px;
    color: white;
}

.cancel_button_container {
    background-color: #F7F7F7;
    width: 30%;
    height: 48px;
    text-align: center;
    align-content: center;
    border-radius: 5px;
    color: black;
    font-weight: bold;
}

button, input, select {
    all:unset;
    font-size: 15px;
}

.container {
    width: 592px;
}

.form_container {
    margin-top: 10px;
    flex-direction: column;
    margin-bottom: 40px;
    display: flex;
    visibility: visible;
    opacity: 1;
}

.v-enter-active,
.v-leave-active {
  transition: all 0.3s ease;
}

.v-enter-from, .v-leave-to {
  transform: translateY(-120%);
  opacity: 0;
}


.form_container * {
    margin: 5px 0px 5px 0px;
    position: relative;
}

.form_container input, .select_container {
    box-sizing: border-box;
    background-color: rgb(255, 255, 255);
    height: 44px;
    width: 100%;
    border-radius: 5px;
    border-width: 1px;
    border-color: rgb(192, 192, 192);
    border-style: solid;
}

.form_container input {
    padding-left: 20px;
}

.dropdown {
    position: relative;
}

.select_container {
    margin-bottom: 0px;
    position: relative;
    padding-left: 20px;
    padding-top: 10px;
    justify-content: center;
    color: grey;
}

.select_value {
    position: absolute;
    top: 5px;
}

.select_options_container {
    margin-top: 0px;
    border-radius: 5px;
    border-width: 0px 1px 1px 1px;
    border-color: rgb(192, 192, 192);
    border-style: solid;
    visibility: hidden;
    opacity: 0;
    position: absolute;
    background-color: white;
    width: 100%;
    z-index: 10;
    pointer-events: none;
}

.show {
  visibility: visible;
  opacity: 1;
  pointer-events: all;
}

.select_options_container ul {
    padding-left: 0px;
    list-style: none;
    align-items: center;
}

.select_options_container ul li:hover {
    background-color: #F7F7F7;
    font-weight: bold;
}

.select_options_container li {
    padding: 5px 20px 5px;
}

.custom_arrow {
    display:block;
    background-color: none;
    position: absolute;
    top:1px;
    right: 15px;
    pointer-events: none;
}

.custom_arrow img {
    height: 18px;
}

.save_user_button_container {
    background-color: black;
    width: 100%;
    height: 48px;
    text-align: center;
    align-content: center;
    border-radius: 5px;
    margin-top: 15px;
}

</style>