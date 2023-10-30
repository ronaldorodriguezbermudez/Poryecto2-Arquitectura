<!-- pages/manufacturers_index.vue -->
<template>
  <div class="container">
   <HeaderView />
   <h3 style="margin-top: 15px">Manufacturers Information</h3>
     <p>This section presents information about Manufacturers</p>
     <ul>
   <li v-for="manufacturer in manufacturers" :key="manufacturer.id2">
     <NuxtLink :to="`/manufacturers/`+manufacturer.id2">{{ manufacturer.nombre }}</NuxtLink>
   </li>
 </ul>

   <FooterView />
 </div>
</template>
<script setup>
const { data: manufacturers } = await useFetch(`https://cms-una.000webhostapp.com/api/content/items/Manufacturers`)
</script>