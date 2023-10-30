<!-- pages/Models/[...slug].vue -->
<template>
  <div class="container">
    <HeaderView />
    <div class="row">
      <div class="three columns">
        <img
          class="u-max-full-width"
          :src="`https://cms-una.000webhostapp.com/storage/uploads${models.image.path}`"
        />
      </div>
      <div class="six columns">
        <h4>{{ model.nombre }}</h4>
        Potencia HP: {{ model.potencia_hp }}; Velocidad Máxima (MPH):
        {{ model.velocidad_maxima_mph }}; Aceleración 0-60 MPH:
        {{ model.aceleracion_0_60_mph }}; Precio (USD): {{ model.precio_usd }}
        <p></p>
        Manufacturer
        <NuxtLink :to="`/manufacturer/` + model.manufacturer._id">
          {{ model.manufacturer }}</NuxtLink
        >
        Designer
        <NuxtLink :to="`/designer/` + model.designer._id">
          {{ model.designer }}</NuxtLink
        >
      </div>
      <div class="two columns"></div>
    </div>
    <FooterView />
  </div>
</template>
<script setup>
	const route = useRoute()
	const { data: model, refresh } = await useFetch(`https://cms-una.000webhostapp.com/api/content/item/models/${route.params.slug}`)
	refresh()
</script>
