<!-- pages/manufacturers_index.vue -->
<template>
    <div class="container">
     <HeaderView />
     <h3 style="margin-top: 15px">Manufacturers Information</h3>
       <p>This section presents information about Manufacturer</p>
     <ul>
       <ContentList path="/manufacturers" v-slot="{ list }">
          <li v-for="manufacter in list" :key="manufacter._path">
           <NuxtLink :to="manufacter._path">{{ manufacter.nombre }}</NuxtLink>
          </li>
        </ContentList>
     </ul>
     <FooterView />
   </div>
  </template>
  