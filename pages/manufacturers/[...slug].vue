<!-- pages/manufacturers/[...slug].vue -->
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
       Fundación: {{ doc.fundacion }}; Sede: {{ doc.sede }}
       <pre></pre>
       
       <h5>Overview</h5>
       <ContentRenderer :value="doc" />
			 <h5>Models</h5>
			  <ul>
          <ContentQuery path="/models" :where="{ manufacturer_id: doc.id }" v-slot="{ data }">
  <ul>
    <li v-for="model in data" :key="model._path">
      <NuxtLink :to="model._path">{{ model.nombre }}</NuxtLink>
    </li>
  </ul>
</ContentQuery>
			 </ul>
			</div>
     </ContentDoc>
   </div>
   <FooterView />
 </div>
</template>
