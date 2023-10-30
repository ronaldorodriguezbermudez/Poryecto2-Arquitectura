<!-- pages/designers/[...slug].vue -->
<template>
  <div class="container">
   <HeaderView />
   <div class="row">
     <div class="three columns">
       <img class="u-max-full-width" :src="`https://cms-una.000webhostapp.com/storage/uploads${designer.image.path}`">
     </div>
     <div class="six columns">
       <h4>{{designer.nombre}}</h4>
       Fundation: {{designer.fundacion}}; 
       Sede: {{designer.sede}};
       <p></p>
     </div>
   </div>
   <FooterView />
 </div>
</template>
<script setup>
	const route = useRoute()
	const { data: designer, refresh } = await useFetch(`https://cms-una.000webhostapp.com/api/content/item/Designers2/${route.params.slug}`)
	refresh()
</script>


