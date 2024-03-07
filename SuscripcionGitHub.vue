<template>
 <div class="card" style="width: 18rem;">
  <img :src="owner.avatar_url" class="card-img-top" alt="...">
  <div class="card-body">
    <h5 class="card-title">{{nombre}}</h5>
    <p class="card-text">{{ owner.login }}</p>
    <a :href="owner.html_url" class="btn btn-primary">Url de Github</a>
  </div>
</div>
</template>

<script setup>
import {defineProps} from 'vue'


defineProps ({
  full_name: String,
  owner: Object
})



</script>

