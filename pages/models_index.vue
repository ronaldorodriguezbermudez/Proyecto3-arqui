<!-- pages/models_index.vue -->
<template>
    <div class="container">
     <HeaderView />
     <h3 style="margin-top: 15px">Models Information</h3>
       <p>This section presents information about Models</p>
      <ul>
        
        <li v-for="model in models" :key="model._id">
          <NuxtLink :to="`/models/`+model._id">{{ model.nombre }}</NuxtLink>
         
        </li>
           
     </ul>
     <FooterView />
   </div>
  </template> 

  <script setup>
    const { data: models } = 
    await useFetch(`https://cms-una.000webhostapp.com/api/content/items/Models?fields={"nombre":true}`)
  </script> 
  