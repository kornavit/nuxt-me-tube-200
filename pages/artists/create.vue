<template>
    <h1 class="text-2xl"> Add Artist</h1>

    <form class="m-4" @submit.prevent="onSubmit()">
        <div>
            <label for="name">Artist Name</label>

            <p v-if="fromErrors.errors" class="text-red-600">
                {{ fromErrors.errors }}
            </p>
            
            <input class="border border-gray-400 p-2 ml-2 rounded-xl"
            v-model="formData.name"
            type="text" id="name" placeholder="Artist Name">
        </div>

        <div class="mt-4">
            <button class="px-4 py-2 border bg-blue-300"
                type="submit">
                Submit
            </button>
        </div>
    </form>
</template>

<script setup lang="ts">
const formData = ref({
    name: ""
})

const fromErrors = ref({
    errors: null
})

async function onSubmit(){
    const { name } = formData.value

    const { data:response, error } = await useMyFetch<any>(
            "artist",{
            method: "POST",
            body: {name},
        }
    )

    if(response.value !== null){
        await navigateTo(`/artists/${response.value.id}`)
    }else{
        console.log(error)
        const { message } = error.value!.data
        // ! บอกว่ามีค่าแน่
        fromErrors.value.errors = message
    }
}
</script>