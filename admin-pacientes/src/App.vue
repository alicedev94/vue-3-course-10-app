<script setup>
import { ref, reactive, onMounted } from 'vue'
import Formulario from './components/Formulario.vue';
import Header from './components/Header.vue';
import Paciente from './components/Paciente.vue';

const paciente = reactive({
    id: null,
    nombre: '',
    propietario: '',
    email: '',
    alta: '',
    sintomas: ''
})

const pacientes = ref([])

// funtions
const guardarDatos = () => {
    pacientes.value.push(paciente)
    guardarLocalStorage()
}

const guardarLocalStorage = () => {
    localStorage.setItem('pacientes', JSON.stringify(pacientes.value))
}

onMounted(() => {
    const pacientesStorage = localStorage.getItem('pacientes')
    if (pacientesStorage) {
        pacientes.value = JSON.parse(pacientesStorage)
    }
})
</script>

<template>
    <div class="container mx-auto mt-20">
        <Header />

        <div class="mt-12 md:flex">
            <Formulario v-model:nombre="paciente.nombre" v-model:propietario="paciente.propietario"
                v-model:email="paciente.email" v-model:alta="paciente.alta" v-model:sintomas="paciente.sintomas"
                @guardar-paciente="guardarDatos" />
            <div class="md:w-1/2 md:h-screen overflow-y-scroll">
                <h3 class="font-black text-3xl text-center">Administra tus Pacientes</h3>

                <div v-if="pacientes.length > 0">

                    <p class="text-lg mt-5 text-center mb-10">
                        Información de
                        <span class="text-indigo-600 font-bold">Pacientes</span>
                    </p>

                    <Paciente v-for="paciente in pacientes" :paciente="paciente" />

                </div>
                <p v-else class="mt-20 text-2xl text-center">No Hay Pacientes</p>
            </div>
        </div>
    </div>
</template>