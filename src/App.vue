<script setup>
import { RouterLink, RouterView } from 'vue-router'
import { ref } from 'vue';
import axios from 'axios';

const navitem = ref([''])

post()

async function post(){
  let url = "https://basic-blog.teamrabbil.com/api/post-categories"
  let res = await axios.get(url)
  navitem.value = res.data

}


</script>

<template>
  <header>

    <nav class="navbar navbar-expand-lg bg-body-tertiary">
  <div class="container-fluid">
    <RouterLink class="navbar-brand" to="/">Mehedi</RouterLink>
    <button class="navbar-toggler" type="button" data-bs-toggle="collapse" data-bs-target="#navbarSupportedContent" aria-controls="navbarSupportedContent" aria-expanded="false" aria-label="Toggle navigation">
      <span class="navbar-toggler-icon"></span>
    </button>
    <div class="collapse navbar-collapse" id="navbarSupportedContent">
      <ul class="navbar-nav me-auto mb-2 mb-lg-0">
        <li class="nav-item" v-for="(item, index) in navitem" :key="index">
          <RouterLink class="nav-link" to="/">{{ item['name'] }}</RouterLink>
        </li>
        </ul>
    </div>
  </div>
</nav>

  </header>

  <RouterView />
</template>

<style scoped>
.navbar {
  padding: 15px 0;
}
.me-auto {
  margin-left: auto !important;
  margin-right: 0 !important;

}

header {
  margin-bottom: 50px;
}


</style>
