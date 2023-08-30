<script setup>

import { ref } from 'vue';
import axios from 'axios';



const lasetItem = ref([''])
laset()

async function laset(){
  let url = "https://basic-blog.teamrabbil.com/api/post-newest"
  let res = await axios.get(url)
  lasetItem.value = res.data

}

const navitem = ref([''])
postList()

async function postList(){
  let url = "https://basic-blog.teamrabbil.com/api/post-list/2"
  let res = await axios.get(url)
  navitem.value = res.data

}


</script>

<template>
  <main>


    
    <div class="container">
      <div class="row">
        <h2>Newest Post</h2>
        <div class="col-md-6 col-lg-4" v-for="(item, index) in lasetItem" :key="index">
          <div class="card">
            <img :src="item.img" class="card-img-top" alt="...">
            <div class="card-body">
              <h5 class="card-title">{{item.title}}</h5>
              <p class="card-text">{{ item.short }}</p>

              <RouterLink class="btn btn-primary" to="/details">see more</RouterLink>
            </div>
          </div>
        </div>
      </div>
    </div>

    <div class="container">
      <div class="row">
        <h2>Post list</h2>
        <div class="col-md-6 col-lg-4" v-for="(item, index) in navitem" :key="index">
          <div class="card">
            <img :src="item.img" class="card-img-top" alt="...">
            <div class="card-body">
              <h5 class="card-title">{{item.title}}</h5>
              <p class="card-text">{{ item.short }}</p>

              <!-- <RouterLink class="btn btn-primary" :to="'/details?id' + item['id']">see more</RouterLink> -->
              <RouterLink class="btn btn-primary" to="/details">see more</RouterLink>
            </div>
          </div>
        </div>
      </div>
    </div>


  </main>
</template>


<style scoped>
.btn-primary {
  margin-top: 15px;
}

.card {
  margin-bottom: 35px;
}

</style>
