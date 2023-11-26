<!-- pages/index.vue -->
<template>
 <div class="container">
   <HeaderView />
   <h2 style="margin-top: 15px">Super Cars</h2>
    <p>This website offers information on super cars Models, Designers and Manufacturers.</p>
    <ul>
      <li> <NuxtLink to="/models_index">Models information</NuxtLink></li>
      <li> <NuxtLink to="/designers_index">Designers information</NuxtLink></li>
      <li> <NuxtLink to="/manufacturers_index">Manufacturers information</NuxtLink></li>
    </ul>
   <FooterView />
 </div>
</template>