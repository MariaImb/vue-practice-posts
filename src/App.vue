<script setup>
import { ref, computed, onMounted } from "vue";
import BlogPost from "./components/BlogPost.vue";
import PaginatePost from "./components/PaginatePost.vue";
import LoadingSpinner from "./components/LoadingSpinner.vue";

const posts = ref([]);
const favorito = ref("");

const postXpage = 5;
const inicio = ref(0);
const fin = ref(postXpage);
const loading = ref(true);

/*Utilizando Fetch*/
// fetch("https://jsonplaceholder.typicode.com/posts")
//     .then((res) => res.json())
//     .then((data) => (posts.value = data))
//     .catch((e) => console.log(e))
//     .finally(() => (loading.value = false));

/*Utilizando async await*/


const fetchData = async() => {
    try {
        const res = await fetch("https://jsonplaceholder.typicode.com/posts");
        posts.value = await res.json();
    } catch (error) {
        console.log(error);
    } finally {
        setTimeout(() => {
            loading.value = false;
        }, 2000);
    }
}

fetchData()

const next = () => {
    inicio.value += postXpage;
    fin.value += postXpage;
};

const prev = () => {
    inicio.value -= postXpage;
    fin.value -= postXpage;
};

const maxLength = computed(() => {
    return posts.value.length;
});
</script>

<template>
    <div class="app-container">
        <LoadingSpinner v-if="loading" />
        <div class="post-container" v-else>
            <h1>Mi post favorito: {{ favorito }}</h1>
            <PaginatePost
                @next="next"
                @prev="prev"
                :inicio="inicio"
                :fin="fin"
                :maxLength="maxLength"
            ></PaginatePost>
            <BlogPost
                v-for="post in posts.slice(inicio, fin)"
                :key="post.id"
                :id="post.id"
                :title="post.title"
                :body="post.body"
            >
            </BlogPost>
        </div>
    </div>
</template>

<style>
.app-container {
    width: 100%;
    height: 100vh;
    display: flex;
    justify-content: center;
}
.post-container {
    width: 60%;
}
</style>
