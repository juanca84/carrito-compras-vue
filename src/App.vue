<template>
  <div id="app">
    <div class="row">
      <div class="col-md-7">
        <div class="row">
          <div class="col-md-6" v-for="pro in productos" :key="pro.id">
            <producto :producto="pro"></producto>
          </div>
        </div>
      </div>
    </div> 
  </div>
</template>

<script>
import Producto from './components/Producto.vue'
import productos from'./productos.json' 
export default {
  name: 'App',
  components: {
    Producto
  },
  data() {
    return{
      productos 
    }
  }
}
</script>

<style>

</style>
