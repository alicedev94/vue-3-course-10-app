<script setup>
const props = defineProps({
    propGuitar: {
        type: Object,
        require: true
    }
});

defineEmits(['agregar-carrito']);
</script>

<template>
    <div class="col-md-6 col-lg-4 my-4 row align-items-center">
        <div class="col-4">
            <img class="img-fluid" :src="'img/' + propGuitar.imagen + '.jpg'" alt="imagen guitarra">
        </div>
        <div class="col-8">
            <h3 class="text-black fs-4 fw-bold text-uppercase">{{ propGuitar.nombre }}</h3>
            <p>{{ propGuitar.descripcion }}</p>
            <p class="fw-black text-primary fs-3">${{ propGuitar.precio }}</p>
            <button type="button" class="btn btn-dark w-100" @click="$emit('agregar-carrito', propGuitar)">
                Agregar al Carrito
            </button>
        </div>
    </div>
</template>


