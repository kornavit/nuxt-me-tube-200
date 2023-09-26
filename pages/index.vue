<template>
    <NuxtLayout name="about">
        <h1>Hello World</h1>
    </NuxtLayout>

    <Counter name="One"></Counter>
    <Counter :name="`Counter` + `Two`"></Counter>

    <h1 class="text-3xl font-bold underline">
        Hello world!
    </h1>
    <img class="w-48" src="~/assets/img/cat.jpg" alt="">

    <div class="my-8"></div>

    <!-- เอาไปใช้จริงตรง public -->
    <img class="w-72" src="/images/cat.jpg" alt="">
</template>