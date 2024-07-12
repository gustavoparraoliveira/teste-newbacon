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
  position: relative;
  justify-self: center;
  width: 592px;
  align-items: center;
  display: block;
  justify-content: center;
  margin-left: 10px;
}

</style>