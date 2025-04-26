<template>
    <div>
        <h2>reactive and watchEffect</h2>
        <input v-model="formData.name" placeholder="Name">
        <P>{{ formData.name }}</P>
        <input v-model="formData.city" placeholder="City">
        <p>{{ formData.city }}</p>
    </div>
</template>

<script setup>
import { reactive, watchEffect} from 'vue'

const formData = reactive({
    name : "",
    age : "",
    city : ""
})

watchEffect(()=>{
    console.log(`Name: ${formData.name}, City: ${formData.city}`)
})
</script>