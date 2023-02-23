<script setup>

import {ref, computed} from "vue"

 /* const name = "VUE dinamico";
  const styeleColor = "color: blue";
  const arrayColors = ["blue", "red", "peru"];
  const active = false;
  //const arrayFrutas = ["🍎", "🍌", "🍉", "🍓", "🍒"];
  const arrayFrutas = [
    {
        name: "Manzana",
        price: "$1.00",
        description: "Una manzana",
        stock: 0,
    },
    {
        name: "Pera",
        price: "$2.00",
        description: "Una pera",
        stock: 10,
    },
    {
        name: "Naranja",
        price: "$3.00",
        description: "Una naranja",
        stock: 20,
    },
];
/*
  const objectFruta = {
              name: "Manzana",
              price: "$1.00",
              description: "Una manzana",
              id: 1,
          };
*/
  
  const counter = ref(0);
  const repeatednum = ref(false);
  const arrayfavnumbers = ref([]);
  const arraycolor = ["green", "red"];
        

// Methods
/*
  const handleclick = (message) => {
    console.log(message);
  }
*/

  const increment = () => {
    counter.value++;
  }
  const decrement = () => {
    counter.value--;
  }
  const reset = () => {
    counter.value = 0;
  }
  const addnumber = () => {
    arrayfavnumbers.value.push(counter.value);
  }

//Computed
  const classCounter = computed(() => {
    arrayfavnumbers.value.indexOf(counter.value) === -1 ? repeatednum.value = false :  repeatednum.value = true;
    return counter.value > 0 ? 'positive' : counter.value != 0 ? 'negative' : 'zero' ;
  });



</script>

<template>
<!--  
  <h1>
    Hola {{ name.toLowerCase()}}
  </h1>
  <h2 :style="`color: ${arrayColors[0]}`">
    Soy azul
  </h2>
  <h3>
    {{ arrayColors }}
  </h3>
  <h2>
    {{  active ? "ON" : "OFF" }}
  </h2>
  <p v-if="active">
    "ON"
  </p>
  <p v-else>
    "OFF"
  </p>    
  <h2 v-show="active">
    ON con v-show
  </h2>
  


  <h1>
    <li v-for="(fruta) in arrayFrutas " :key="fruta.id">
      {{ fruta.description }} cuesta {{ fruta.price }}

    </li>
  </h1>

  <h3>
    <li v-for="(value, propiedad, index) in objectFruta" :key="value"> 
      {{index}} - {{ propiedad }}: {{ value}}
      
    </li>

  </h3>


  <ul>
    <template v-for=" item in arrayFrutas" :key="item.name">
      <li v-if="item.stock > 0" >
        {{item.name}} - {{ item.price }}
      </li>
    </template>
  </ul>


  <button @click.left="handleclick('Hola mundo')">
    Activame boton izq
  </button>
  <button @click.middle="handleclick('Hola mundo')">
    Activame boton rueda
  </button>
  <button @click.right.prevent="handleclick('Hola mundo')">
    Activame boton der
  </button>
-->
  <div class="container text-center mt-3">
    <h1>Hola Vue</h1>

    <h2 :class="classCounter" >
      {{ counter }}
    </h2>
    <div class="btn-group">
      <button @click="increment()" class="btn btn-secondary">
      Aumentar contador
      </button>
      <button @click="decrement()" class="btn btn-secondary">
        Disminuir contador
      </button>
      <button @click="reset()" class="btn btn-secondary">
        Reset contador
      </button>
      <button @click="addnumber()" :disabled="repeatednum" class="btn btn-secondary"> 
        Numero favorito
      </button>
    </div>
    <ul class="list-group mt">
      <li v-for="(numero, index) in arrayfavnumbers" :key="index" class="list-group-item">
        {{ numero }}
      </li> 
    </ul>
  </div>
  


</template>


<style>

  .positive {
    color: green;
  }

  .negative {
    color: red;
  }

  .zero {
    color: blueviolet;
  }

</style>