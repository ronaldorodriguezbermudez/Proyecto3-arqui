<!-- pages/manufacturers_index.vue -->
<template>
    <div class="container">
     <HeaderView />
     <h3 style="margin-top: 15px">Manufacturers Information</h3>
       <p>This section presents information about Manufacturer</p>
     <ul>
       
          <li v-for="manufacter in manufacturers" :key="manufacter._id">
           <NuxtLink :to="`/manufacturers/`+manufacter._id">{{ manufacter.nombre }}</NuxtLink>
          </li>
     </ul>
     <FooterView />
   </div>
  </template>

  <script setup>
  const { data: manufacturers} = 
    await useFetch(`https://cms-una.000webhostapp.com/api/content/items/Manufacturers?fields={"nombre":true}`)
</script>