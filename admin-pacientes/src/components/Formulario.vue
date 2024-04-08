<script setup>
const props = defineProps({
    nombre: {
        type: String,
        required: true
    },
    propietario: {
        type: String,
        required: true
    },
    email: {
        type: String,
        required: true
    },
    alta: {
        type: String,
        required: true
    },
    sintomas: {
        type: String,
        required: true
    }
})

const emit = defineEmits(['update:nombre', 'update:propietario', 'update:email', 'update:alta', 'update:sintomas', 'guardar-paciente'])

</script>

<template>
    <div class="md:w-1/2">
        <h2 class="font-black text-3xl text-center">Seguimiento Pacientes</h2>
        <p class="text-lg mt-5 text-center mb-10">
            Añade Pacientes y
            <span class="text-indigo-600 font-bold">Adminístralos</span>
        </p>

        <form @submit.prevent="$emit('guardar-paciente')" class="bg-white shadow-md rounded-lg py-10 px-5 mb-10">
            <div class="mb-5">
                <label for="mascota" class="block text-gray-700 uppercase font-bold">
                    Nombre Mascota
                </label>
                <input id="mascota" type="text" placeholder="Nombre de la mascota"
                    class="border-2 w-full p-2 mt-2 placeholder-gray-400 rounded-t-md" :value="nombre"
                    @input="$emit('update:nombre', $event.target.value)" />

            </div>
            <div class="mb-5">
                <label for="propietario" class="block text-gray-700 uppercase font-bold">
                    Nombre Propietario
                </label>
                <input id="propietario" type="text" placeholder="Nombre del propietario"
                    class="border-2 w-full p-2 mt-2 placeholder-gray-400 rounded-t-md" :value="propietario"
                    @input="$emit('update:propietario', $event.target.value)" />
            </div>
            <div class="mb-5">
                <label for="email" class="block text-gray-700 uppercase font-bold">
                    Email
                </label>
                <input id="email" type="email" placeholder="Email del propietario"
                    class="border-2 w-full p-2 mt-2 placeholder-gray-400 rounded-t-md" :value="email"
                    @input="$emit('update:email', $event.target.value)" />
            </div>
            <div class="mb-5">
                <label for="fechaAlta" class="block text-gray-700 uppercase font-bold">
                    Alta
                </label>
                <input id="fechaAlta" type="date" class="border-2 w-full p-2 mt-2 placeholder-gray-400 rounded-t-md"
                    :value="alta" @input="$emit('update:alta', $event.target.value)" />
            </div>
            <div class="mb-5">
                <label for="sintomas" class="block text-gray-700 uppercase font-bold">
                    Síntomas
                </label>
                <textarea id="sintomas" placeholder="Describe los sintomas"
                    class="border-2 w-full p-2 mt-2 placeholder-gray-400 rounded-t-md resize-none h-40"
                    :value="sintomas" @input="$emit('update:sintomas', $event.target.value)" />
            </div>

            <input type="submit"
                class="bg-indigo-600 w-full p-3 text-white uppercase font-bold hover:bg-indigo-400 cursor-pointer transition-colors"
                value="Registrar Paciente">
        </form>
    </div>
</template>
