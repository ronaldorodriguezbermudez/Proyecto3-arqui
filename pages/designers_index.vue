<!-- pages/designers_index.vue -->
<template>
    <div class="container">
     <HeaderView />
     <h3 style="margin-top: 15px">Designers Information</h3>
       <p>This section presents information about Designers</p>
     <ul>
    
          <li v-for="designer in designers" :key="designer._id">
            <NuxtLink :to="`/designers/`+designer._id">{{ designer.nombre }}</NuxtLink>
          </li>
 
     </ul>
     <FooterView />
   </div>
  </template>
    <script setup>
    const { data: designers } = 
    await useFetch(`https://cms-una.000webhostapp.com/api/content/items/Designers2?fields={"nombre":true}`)
  </script> 