<!-- pages/models_index.vue -->
<template>
    <div class="container">
     <HeaderView />
     <h3 style="margin-top: 15px">Models Information</h3>
       <p>This section presents information about Models</p>
     <ul>
       <ContentList path="/models" v-slot="{ list }">
          <li v-for="model in list" :key="model._path">
           <NuxtLink :to="model._path">{{ model.nombre }}</NuxtLink>
          </li>
        </ContentList>
     </ul>
     <FooterView />
   </div>
  </template>
  