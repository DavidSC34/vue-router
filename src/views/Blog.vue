<template>
  <Titulo texto="Titulo de mi blog"/>
  <!-- <button @click="consumirApi">Cosnumir API</button> -->
  <div v-for="item in arrayBlog" :key="item.id">
      <router-link :to="`/blog/${item.id}`">
      {{ item.id }} - {{ item.title }}

      </router-link>
  </div>
</template>

<script>
import Titulo from "../components/Titulo";
    export default {
        name:'Blog',
        components: {
            Titulo,
        },
        data() {
            return {
                arrayBlog: []
            }  
        },
        methods: {
            async consumirApi() {
                try {
                    const data = await fetch('https://jsonplaceholder.typicode.com/posts')
                    const array = await data.json();
                    this.arrayBlog = array;
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

<style lang="scss" scoped>

</style>