<template>
  <div id="app">
    <div class="row">
      <div class="col-md-7">
        <div class="row">
          <div class="col-md-6" v-for="pro in productos" :key="pro.id">
            <producto :producto="pro" v-on:agregar-carro="agregarProdCarro" :estaEnCarrito="estaEnCarrito(pro)"></producto>
          </div>
        </div>
      </div>
      <div class="col-md-5 my-5">
        <div class="row">
          <carrito :items="carrito" v-on:remover-item="removerProducto" v-on:pagar="pagar"/>
        </div>
      </div>
    </div> 
  </div>
</template>

<script>
import Producto from './components/Producto.vue'
import Carrito from './components/Carrito.vue'
import productos from'./productos.json' 
export default {
  name: 'App',
  components: {
    Producto,
    Carrito
  },
  data() {
    return{
      productos,
      carrito:[]
    }
  },
  methods:{
    agregarProdCarro(producto){
      this.carrito.push(producto);
    },
    estaEnCarrito(producto){
      const item = this.carrito.find(item => item.id === producto.id)
      if(item) {
        return true;
      } else {
        return false;
      }
    },
    removerProducto(producto){
      this.carrito = this.carrito.filter(item => item.id != producto.id)

    },
    pagar(){
      this.carrito = [];
      alert("Venta Completada!!!")
    }
  }
}
</script>

<style>

</style>
