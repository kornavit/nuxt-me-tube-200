<template>
    <h1>{{ pageTitle }}</h1>

    <div class="text-3xl m-8">
        {{ artist.name }}
    </div>

    <div class="mx-16 my-4 border p-4 text-xl rounded-xl hover:bg-green-200" v-for="song in artist.songs" :key="song.id">
        {{ song.title }}
    </div>
</template>

<script setup type="ts">
const route = useRoute();
const config = useRuntimeConfig();
const pageTitle = `Artist ID: ${route.params.id}`

const { data:artist, error } = await useFetch(
    `artist/${route.params.id}`,{
        baseURL:config.public.apiBaseURL
    }
)

if(artist.value === null){
    const {statusCode, statusMessage } = error.value
    console.log(statusCode, statusMessage)
    if(statusCode === 404){
        await navigateTo("/artists")
    }
}else{
    console.log(artist.value);
}
</script>