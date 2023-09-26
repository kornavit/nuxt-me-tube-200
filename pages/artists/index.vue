<template>
    <h1>Artists</h1>

    <div v-if="pending">
        Loading...
    </div>

    <div v-else class="my-2 mx-8">
        <div v-for="artist in artists" :key="artist.id" class="my-2 mx-8 border p-4 rounded-xl hover:bg-green-200">
            <nuxt-link class="hover:text-blue-500"
                :to="`/artists/${artist.id}`">
                {{ artist.name }}
            </nuxt-link>
        </div>
    </div>
</template>

<script setup lang="ts">
const {data: artists , pending } = await useMyFetch<any>("artist", {})
</script>