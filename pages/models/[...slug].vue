<!-- pages/Models/[...slug].vue -->
<template>
  <div class="container">
    <HeaderView />
    <div class="row">
      <ContentDoc v-slot="{ doc }">
        <div class="three columns">
          <img class="u-max-full-width" :src="'/images/' + doc.imagen">
        </div>
        <div class="six columns">
          <h4>{{ doc.nombre }}</h4>
          Potencia HP: {{ doc.potencia_hp }}; Velocidad Máxima (MPH): {{ doc.velocidad_maxima_mph }};
          Aceleración 0-60 MPH: {{ doc.aceleracion_0_60_mph }};
          Precio (USD): {{ doc.precio_usd }}
         
          <pre></pre>

          <h5>Detalles Técnicos</h5>
          <ContentRenderer :value="doc" />

          <h5>Manufacturer</h5>
			  <ul>
          <ul>
            <ContentQuery path="/manufacturers" :where="{ id: doc.manufacturer_id }" v-slot="{ data }">
              <li v-for="manufacter in data" :key="manufacter._path">
                <NuxtLink :to="manufacter._path">{{ manufacter.nombre }}</NuxtLink>
              </li>
            </ContentQuery>
          </ul>
            <h5>Designer</h5>
			  <ul>
            <ContentQuery path="/designer" :where="{ id: doc.designer_id }" v-slot="{ data }">
              <li v-for="designer in data" :key="designer._path">
                <NuxtLink :to="designer._path">{{ designer.nombre }}</NuxtLink>
              </li> 
            </ContentQuery>
          </ul>
           
          </ul>
        </div>
      </ContentDoc>
    </div>
    <FooterView />
  </div>
</template>

