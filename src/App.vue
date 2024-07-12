<script setup>

import { RouterLink, RouterView } from 'vue-router'

import HomeView from './views/HomeView.vue'
import UserDetailsView from './views/UserDetailsView.vue';
import UserEditView from './views/UserEditView.vue';

</script>

<template>
  <RouterView />
</template>

<style scoped>

* {
  font-family: Montserrat;
}

 header {
  line-height: 1.5;
  max-height: 100vh;
}
</style>
