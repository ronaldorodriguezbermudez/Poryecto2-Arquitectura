<!-- pages/manufacturers/[...slug].vue -->

<template>
  <div class="container">
   <HeaderView />
   <div class="row">
     <div class="three columns">
       <img class="u-max-full-width" :src="`https://cms-una.000webhostapp.com/storage/uploads${manufacturer.image.path}`">
     </div>
     <div class="six columns">
       <h4>{{manufacturer.nombre}}</h4>
       Fundation: {{manufacturer.fundacion}}; 
       Sede: {{manufacturer.sede}}
       Models <NuxtLink :to="`/models/`+manufacturer.manufacturer._id">
       {{models.manufacturer}}</NuxtLink>
			 <p></p>
  
     </div>
     <div class="two columns"></div>
   </div>
   <FooterView />
 </div>
</template>
<script setup>
	const route = useRoute()
	const { data: manufacturer, refresh } = await useFetch(`https://cms-una.000webhostapp.com/api/content/item/manufacturers/${route.params.slug}`)
	refresh()
</script>
