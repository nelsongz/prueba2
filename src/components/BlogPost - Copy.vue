<script setup>
// defineProps(['title','pie','colorText'])

defineProps({
    title: String,
    id: Number,
    pie: {
        type: String,
        default: "Sin descripcion"
    }
})
</script>

<template>
    <div class="card">
        <div class="card-body">
            <h5 class="card-title">{{title}}</h5>
            <p>{{pie}}</p>
        </div>
    </div>
</template>

<!-- <template>
    <div class="card">
        <div class="card-body">
            <h5 
                class="card-title"
                :class="`text-${colorText}`"
                >
                {{title}}
            </h5>
            <p>Lorem ipsum dolor sit amet.</p>
            <h6>{{pie}}</h6>
        </div>
    </div>
</template> -->