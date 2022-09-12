<script setup>

    defineProps({
        title: String,
        id: Number,
        pie: {
            type: String,
            default: "Sin descripcion"
        }
    })

    const emit = defineEmits(['metodoFavorito'])
</script>

<template>
    <div class="card">
        <div class="card-body">
            <h5 class="card-title">{{title}}</h5>
            <p>{{pie}}</p>
            <button 
                @click="emit('metodoFavorito', title)"
                class="btn btn-outline-primary">
                Favorito
            </button>
        </div>
    </div>
</template>