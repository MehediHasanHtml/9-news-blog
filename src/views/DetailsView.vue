<script setup>

import { ref } from 'vue';
import axios from 'axios';


const details = ref([''])
postDetails()

async function postDetails(){
  let url = "https://basic-blog.teamrabbil.com/api/post-list/2"
  let res = await axios.get(url)
  details.value = res.data

}


</script>

<template>
  <main>

    <div class="container">
      <div class="row">
        <div class="col-12">
          <div class="deatails">
            <div class="card" v-for="(item, index2) in details" :key="index2">
            <img :src="item.img" class="card-img-top" alt="...">
            <div class="card-body">
              <h5 class="card-title">{{item.title}}</h5>
              <p class="card-text">{{ item.short }}</p>
            </div>
          </div>
          </div>
        </div>
      </div>
    </div>

  </main>
</template>


<style scoped>

.card {
  margin-bottom: 35px;
}

</style>
