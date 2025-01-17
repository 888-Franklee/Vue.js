<script setup>
import {ref, watch} from 'vue'
const count = ref(0)
const setCount = ()=>{
    count.value++
}

watch(count,(newVal, oldVal) => {
    console.log(`countが変更されました 新：${newVal} 旧：${oldVal}`)
})

</script>

<template>
    <div>
        <button @click="setCount">{{ count }}</button>
    </div>
</template>