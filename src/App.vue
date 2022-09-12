<script setup>
    // Librerias VUE o externos
    import {onMounted, ref} from "vue";

    // Componentes propios
    import BlogPost from './components/BlogPost.vue';
    import PaginatePost from './components/PaginatePost.vue';
    import LoadingSpinner from "./components/LoadingSpinner.vue";

    // Variables/Constantes/Funciones locales
    const cambiarFavorito = (title) => {
        favorito.value = title
    }
    const postXpage = 20
    const next = () => { 
        inicio.value = inicio.value + postXpage
        fin.value += postXpage
    }
    const prev = () => { 
        inicio.value = inicio.value - postXpage
        fin.value += - postXpage
    }

    // Datos reactivos
    const posts = ref([])
    const favorito = ref('')
    const inicio = ref(0)
    const fin = ref(postXpage)
    const loading = ref(true)

    // Datos externos
    // onMounted(async() => { 
    //     try {
    //         const res = await fetch('https://jsonplaceholder.typicode.com/posts')
    //         posts.value = await res.json()
    //     } catch (error) {
    //         console.log(error)
    //     } finally {
    //         setTimeout(() => {
    //              loading.value = false
    //          },2000)
    //     }
    // })

    // fetch('https://jsonplaceholder.typicode.com/posts')
    //     .then(res => res.json())
    //     .then(data => posts.value = data)
    //     .catch((e) => console.log(e))
    //     .finally(() => {
    //         setTimeout(() => {
    //             loading.value = false
    //         },2000)
    //     })

    onMounted(() => {
        fetchData()
    })
    const fetchData = async() => {
        try {
            const res = await fetch('https://jsonplaceholder.typicode.com/posts')
            posts.value = await res.json()
        } catch (error) {
            console.log(error)
        } finally {
            setTimeout(() => {
                 loading.value = false
             },2000)
        }
    }
    //fetchData()
    
</script>

<template>
    <LoadingSpinner v-if="loading"/>
    <div class="cotainer" v-else>
        <h1>APP</h1>
        <h2>Mis Posts favoritos: {{favorito}}</h2>
        <br />
        <PaginatePost
            class="mb-2"
            @next="next"
            @prev="prev"
            :inicio="inicio"
            :fin="fin"
            :maxLength="posts.length"
        />
        <BlogPost
            v-for="post in posts.slice(inicio,fin)"
            :key="post.id"
            :id="post.id"
            :title="post.title"
            :body="post.body"
            @metodoFavorito="cambiarFavorito"
            class="mb-2"
        ></BlogPost>
    </div>
</template>