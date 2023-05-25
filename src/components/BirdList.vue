<template>
    <div>
      <h1>Pájaros de Chile</h1>

      <!--lista de pájaros de la Api-->
      <ul>
        <!-- Iteración sobre el array birds listado de nombres-->
        <li v-for="bird in birds" :key="bird.id">{{ bird.name }}</li>
      </ul>
    </div>
  </template>
  
<script>
  export default {

    name: 'BirdList', 
    data() {
      return {
        // Array de pájaros de Chile
        birds: []
      }
    },
    mounted() {
      this.fetchBirds()
    },
    
    methods: {
      // Metodo para obtener los pajaros mediante una solicitud HTTP
      fetchBirds() {
        fetch('https://aves.ninjas.cl/api/birds')
          .then(response => response.json())
          .then(data => {
            // Asignar los datos de los pajaros al array 'birds'
            this.birds = data
          })
          .catch(error => {
            console.error('Error:', error)
          })
      }
    }
  }
  </script>
 <style>
 
 </style>
  