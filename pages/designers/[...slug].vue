<!-- pages/designers/[...slug].vue -->
<template>
  <div class="container">
   <HeaderView />
   <div class="row">

     <div class="three columns">
      <img class="u-max-full-width" 
         :src="`https://cms-una.000webhostapp.com/storage/uploads${designer.imagen.path}`">
     </div>
     <div class="six columns">
       <h4>{{ designer.nombre }}</h4>
       Fundación: {{ designer.fundacion }}; 
       <br>
       Sede: {{ designer.sede }}
       <pre></pre>
       

			 <h5>Models</h5>
			  <ul>           
              <li v-for="model in models" :key="model._id">
                <NuxtLink :to="`/models/`+ model._id">{{ model.nombre }}</NuxtLink>
              </li>          
			 </ul>
			</div>
   </div>
   <FooterView />
 </div>
</template>


<script setup>
  const route = useRoute()
  const { data: designer, refresh: rDesigner } = 
    await useFetch(`https://cms-una.000webhostapp.com/api/content/item/Designers2/${route.params.slug}`)
    rDesigner()
  const { data: models, refresh: rModels } = 
    await useFetch(`https://cms-una.000webhostapp.com/api/content/items/Models?filter={"designer_id._id":"${route.params.slug}"}&fields={"nombre":true}`)
    rModels()
</script>



