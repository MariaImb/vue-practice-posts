<script setup>
import { ref, computed} from "vue";
import BlogPost from "./components/BlogPost.vue";
import PaginatePost from "./components/PaginatePost.vue"

const posts = ref([])
const favorito = ref("");

const postXpage = 5;
const inicio = ref(0);
const fin = ref(postXpage)

fetch("https://jsonplaceholder.typicode.com/posts")
    .then(res => res.json())
    .then(data => posts.value = data)


const next = () => {
    inicio.value += postXpage
    fin.value +=  postXpage
}

const prev = () => {
    inicio.value -= postXpage
    fin.value -= postXpage
}

const maxLength = computed(()=> {
    return posts.value.length
})
</script>

<template>
    <div class="app-container">
        <div class="post-container">
            <h1>Mi post favorito: {{ favorito }}</h1>
            <PaginatePost @next="next" @prev="prev" :inicio="inicio" :fin="fin" :maxLength="maxLength"></PaginatePost>
            <BlogPost v-for="post in posts.slice(inicio, fin)"
            :key = post.id
            :id = post.id
            :title = post.title
            :body = post.body
            > </BlogPost>
        </div>
    </div>
</template>

<style>
.app-container {
    width: 100%;
    display: flex;
    justify-content: center;
}
.post-container {
    width: 60%;
}
</style>
