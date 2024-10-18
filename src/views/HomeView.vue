<template>
    <div class="home">
      <NewUserForm />
      <UserList /> 
    </div>
</template>

<script setup>

import UserList from '../components/UserList.vue'
import NewUserForm from '../components/NewUserForm.vue'

</script>

<style>

.home {
  width: 592px;
  display: flex;
  margin: auto;

}

</style>