<template>
  <Titulo texto="Ruta con parametros" />
  <h2>Parametro {{$route.params.id}}</h2>
  <h2>{{articulo.title}}</h2>
  <p>{{articulo.id}} - {{articulo.body}}</p>
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
       
          const data = await fetch(`https://jsonplaceholder.typicode.com/posts/${this.$route.params.id}`);
          const postData = await data.json();
          // console.log(postData);
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