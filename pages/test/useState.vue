<template>
    <div class="flex m-8 justify-between w-1/2">
        <UseStateCounter @changeUp="onChangeUp"
            name="UseState First">
        </UseStateCounter>
        <UseStateCounter @changeUp="onChangeUp" 
            name="UseState Second">
        </UseStateCounter>
        <UseStateCounter @changeUp="onChangeUp" @changeDown="onChangeDown"
            name="UseState Third">
        </UseStateCounter>
    </div>

    <div>
      Message : {{ message }} <br>
      AppTheme : {{ appTheme }} <br>
      Hello : {{ hello }}
    </div>
</template>

<script setup lang="ts">
import { useLocalStorage , useSessionStorage } from '@vueuse/core'
const message = ref("")
const appTheme = useLocalStorage('app-theme', null)
const hello = useSessionStorage('hello' , null)


function onChangeUp(name: string , count: number){
    message.value = `counter ${name} has been changed up to ${count}`
}
function onChangeDown(name: string , count: number){
    message.value = `counter ${name} has been changed down to ${count}`
}
</script>