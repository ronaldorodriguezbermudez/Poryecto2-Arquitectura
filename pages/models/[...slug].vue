<!-- pages/Models/[...slug].vue -->

<template>
  <div class="container">
   <HeaderView />
   <div class="row">
     <div class="three columns">
       <img class="u-max-full-width" 
         :src="`https://cms-una.000webhostapp.com/storage/uploads${model.imagen.path}`">
     </div>
     <div class="six columns">
       <h4>{{model.nombre}}</h4>
       by <NuxtLink :to="`/designers/`+model.designer_id._id">{{model.designer_name}}</NuxtLink><br>
       Potencia: {{model.potencia_hp}} <br>
       Velocidad: {{model.velocidad_maxima_mph}}<br>
       Aceleración: {{model.aceleracion_0_60_mph}} <br>
       Precio: {{model.precio}} <br>
       Manufacturer <NuxtLink :to="`/manufacturers/`+model.manufacturer_id._id">{{model.manufacturer_name}}</NuxtLink><br>

     </div>
     <div class="two columns"></div>
   </div>
   <FooterView />
 </div>
</template>
<script>
	export default {
		mounted () {
		    document.addEventListener('snipcart.ready', function () {
		      this.addItemEvent = window.Snipcart.events.on('item.added', (cartItem) => {
		        // console.log(cartItem)
		      })
		    })
		  }
	}
</script>
<script setup>
  const route = useRoute()
  const { data: model, refresh } = 
    await useFetch(`https://cms-una.000webhostapp.com/api/content/item/Models/${route.params.slug}`)
  refresh()
</script>

