<template>
    <h1>Artists</h1>

    <img style="width: 200px; height: 200px" :src="bigImage" alt="">
    {{ bigImage }}
    <div v-for="artist of artists" :key="artist.id">
        <h3 @click="change(artist.image)">{{ artist.name }}</h3>
        <img style="width: 100px; height: 100px;" :src="artist.image" alt="">
    </div>
</template>

<script setup lang="ts">

const bigImage = useState<string>(undefined)
bigImage.value = "https://upload.wikimedia.org/wikipedia/commons/thumb/4/48/RedCat_8727.jpg/1200px-RedCat_8727.jpg"

const change = function(_image: string){
    console.log(_image)
    bigImage.value = _image
}

    const artists = [
        {
            id:1,
            name: "black and brown",
            image: "https://cdn.britannica.com/39/7139-050-A88818BB/Himalayan-chocolate-point.jpg"
        },
        {
            id: 2,
            name: "orange",
            image: "https://hips.hearstapps.com/hmg-prod/images/beautiful-smooth-haired-red-cat-lies-on-the-sofa-royalty-free-image-1678488026.jpg?crop=1xw:0.84415xh;center,top"
        },
        {
            id: 3,
            name: "cats",
            image: "https://i.guim.co.uk/img/media/26392d05302e02f7bf4eb143bb84c8097d09144b/446_167_3683_2210/master/3683.jpg?width=1200&quality=85&auto=format&fit=max&s=a52bbe202f57ac0f5ff7f47166906403"
        }
    ]
</script>