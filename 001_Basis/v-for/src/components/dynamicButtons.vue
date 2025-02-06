<template>
    <h3>DynamicButtons</h3>
    <div>
        <button v-for="(label,index) in button" :key="index" @click="handleClick(label)">
            {{ label }}
        </button>

    </div>
</template>

<script setup>
const button = ["Button1", "Button2", "Button3"]
const handleClick = (label)=>{
    alert(`You clicked: ${label}`)
}
</script>