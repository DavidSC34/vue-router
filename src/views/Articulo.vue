<template>
  <Titulo texto="Ruta con parametros" />
  <h2>Parametro {{$route.params.id}}</h2>
  <h2>{{articulo.titulo}}</h2>
  <p>{{articulo.cuerpo}}</p>
</template>

<script>
import Titulo from "../components/Titulo"

export default {
  name:'Articulo',
  data() {
    return {
      articulo:{}
    }
  },
  components: {
    Titulo,
  },
  methods: {
    async consumirApi() {

      try {
        const id = this.$route.params.id;
          const data = await fetch('https://jsonplaceholder.typicode.com/posts/'+id);
          const postData = await data.json();
          this.articulo = postData;
          

      } catch (error) {
        console.log(error)
      }
      
    }
  },
  created(){
    this.consumirApi();
  }
}
</script>

<style>

</style>