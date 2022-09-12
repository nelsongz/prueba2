<script setup>
    import ButtonCounter from './components/ButtonCounter.vue';
    import BlogPost from './components/BlogPost.vue';
    import {ref} from "vue";

    const posts = ref([
        {title: "Post 1", pie: "solo para Post 1"},
        {title: "Post 2", pie: "solo para Post 2"},
        {title: "Post 3", pie: "solo para Post 3"},
        {title: "Post 4"}
    ])
</script>

<template>
    <h1>APP</h1>
    <br />
    <ButtonCounter />
    <ButtonCounter />

    <BlogPost
        v-for="post in posts"
        :key="post.title"
        :title="post.title"
        :pie="post.pie"
    ></BlogPost>

    <!-- <BlogPost title="Post 1" pie="solo para Post 1" colorText="primary"/>
    <BlogPost title="Post 2" pie="solo para Post 2" colorText="success"/>
    <BlogPost title="Post 3" pie="solo para Post 3" colorText="warning"/>
    <BlogPost title="Post 4" colorText="primary"/> -->
</template>