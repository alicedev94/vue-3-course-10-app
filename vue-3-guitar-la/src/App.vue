<script setup>
import { reactive, onMounted, ref } from 'vue'
import { db } from '../data/guitars'
import Product from './components/Product.vue';
import Header from './components/Header.vue';
import Footer from './components/Footer.vue';

const state = reactive({
  guitars: []
})

const carrito = ref([]);

onMounted(() => {
  state.guitars = db
  if (localStorage.carrito.length > 0) {
    carrito.value = JSON.parse(localStorage.getItem('carrito'))
  }
});

const guardarLocalStorage = () => {
  localStorage.setItem('carrito', JSON.stringify(carrito.value))
}

const agregarCarrito = (guitarra) => {
  const existeCarrito = carrito.value.findIndex(product => product.id === guitarra.id);
  if (existeCarrito >= 0) {
    // Ya existe el producto en el carrito
    carrito.value[existeCarrito].cantidad++
  } else {
    // El producto aun no ha sido agregado al carrito
    guitarra.cantidad = 1;
    carrito.value.push(guitarra);
  }

  guardarLocalStorage();
}

const eliminarProducto = (productId) => {
  let numerOne = 1;
  const index = carrito.value.findIndex((product) => product.id === productId);
  carrito.value.splice(index, numerOne);

  guardarLocalStorage();
}

const aumentarCarrito = (productId) => {
  const index = carrito.value.findIndex((product) => product.id === productId);
  carrito.value[index].cantidad++

  guardarLocalStorage();
}

const decrementarCarrito = (productId) => {
  const index = carrito.value.findIndex((product) => product.id === productId);
  if (carrito.value[index].cantidad <= 1) return
  carrito.value[index].cantidad--

  guardarLocalStorage();
}

const vaciarCarrito = () => {
  if (carrito.value.length <= 0) return
  carrito.value = []

  guardarLocalStorage();
}
</script>

<template>
  <Header :propCarrito="carrito" @eliminar-carrito="eliminarProducto" @decrementar-carrito="decrementarCarrito"
    @aumentar-carrito="aumentarCarrito" @vaciar-carrito="vaciarCarrito" />

  <body>
    <main class="container-xl mt-5">
      <h2 class="text-center">Nuestra Colección</h2>
      <div class="row mt-5">
        <Product v-for="guitar in state.guitars" :propGuitar="guitar" @agregar-carrito="agregarCarrito" />
      </div>
    </main>
  </body>
  <Footer />
</template>
