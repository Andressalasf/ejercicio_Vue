<script setup>
  import { ref } from 'vue';


  const productos = ref([{name: "Perico", cant: 5, value: 2000, day: 1}, {name:"Bazuco", cant:2, value:10000, day: 20}])

  const cantidadTotal =  ref(0)
  const precioTotal = ref(0)

function amountProducts(){
  
  productos.value.forEach(produc => {
   
    cantidadTotal.value += produc.cant
    precioTotal.value += produc.value


   
    
  }); 


  
  
}
</script>

<template>
    <div class="contenedor">
      
        <div v-for="(produc , index)  in productos" :key="index">
            <div v-show="produc.day > 0 && produc.cant > 0" class="produc"  >
                <p>{{ produc.name }}   <span :class="{vencer: produc.day > 0 && produc.day <=3}" v-show="produc.day > 0 && produc.day <=3"> esta apunto de vencer</span></p>
                <p>Cantidad:  <span>{{ produc.cant }}</span></p>
                <p>Precio:  <span>{{ produc.value }}</span></p>
                <p>Dias para vencer:  <span>{{ produc.day }}</span> </p>
               
            </div>
            
            
        </div>
        <div  class="total"> 
          <div class="tproduc" @click="amountProducts()">Ver cantidad de productos y el valor total</div>
          <p> Cantidad de productos: <span>{{ cantidadTotal }}</span></p> <p>Precio total <span>{{ precioTotal }}</span></p>
        </div>
    </div>
</template>

<style scoped>

  .vencer{
    background-color: red;
  }
 .contenedor{
  width: 60%;
  height: 100%;
  background-color: aquamarine;
  margin: 0 auto;
  text-align: center;
  
}

.contenedor .produc{
  width: 60%;
  height: 80%;
  background-color: aqua;
  margin: 0 auto;
}

.contenedor .total{
  width: 60%;
  height: 100px;
  background-color: bisque;
  margin: 0 auto;
}

.contenedor .total .tproduc{
  background-color: brown;
  width: 50%;
  border-radius: 30px;
  margin: 0 auto;
  cursor: pointer;
}



</style>
