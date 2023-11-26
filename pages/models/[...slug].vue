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

       <button class="
              snipcart-add-item
              mt-4
              bg-white
              border border-gray-200
              d
              hover:shadow-lg
              text-gray-700
              font-semibold
              py-2
              px-4
              rounded
              shadow"
					:data-item-id="model._id"
					:data-item-price="model.precio"
					:data-item-description="model.nombre"
					:data-item-image="'https://cms-una.000webhostapp.com/storage/uploads/'+model.imagen.path"
					:data-item-name="model.nombre"
					>Buy Me!</button>
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

