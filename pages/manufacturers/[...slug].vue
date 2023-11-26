<!-- pages/manufacturers/[...slug].vue -->
<template>
  <div class="container">
   <HeaderView />
   <div class="row">

     <div class="three columns">
      <img class="u-max-full-width" 
         :src="`https://cms-una.000webhostapp.com/storage/uploads${manufacturer.imagen.path}`">
     </div>
     <div class="six columns">
       <h4>{{ manufacturer.nombre }}</h4>
       Fundación: {{ manufacturer.fundacion }}; 
       <br>
       Sede: {{ manufacturer.sede }}
       <pre></pre>
       

			 <h5>Models</h5>
			  <ul>           
              <li v-for="model in models" :key="model._id">
                <NuxtLink :to="`/models/`+ model._id">{{ model.nombre }}</NuxtLink>
              </li>          
			 </ul>
			</div>

   </div>
   <div id="utterances"></div>
   <FooterView />
 </div>
</template>
<script setup>
  const route = useRoute()
  const { data: manufacturer, refresh: rManufacturer } = 
    await useFetch(`https://cms-una.000webhostapp.com/api/content/item/Manufacturers/${route.params.slug}`)
    rManufacturer()
  const { data: models, refresh: rModels } = 
    await useFetch(`https://cms-una.000webhostapp.com/api/content/items/Models?filter={"manufacturer_id._id":"${route.params.slug}"}&fields={"nombre":true}`)
    rModels()
    onMounted(() => {
    const s = document.createElement('script');
    s.src = 'https://utteranc.es/client.js';
    s.setAttribute('repo', 'ronaldorodriguezbermudez/gestion-comentarios-supercars');
    s.setAttribute('issue-term', 'pathname');
    s.setAttribute('theme', 'github-light');
    s.setAttribute('crossorigin', 'anonymous');
    s.async = true;
    document.getElementById('utterances').appendChild(s);
  });
</script>
