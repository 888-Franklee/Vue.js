<template>
    <div>
        <input type="checkbox" v-model="isChecked" @change="isCheckedOk">
        <p>チェックの状態：{{ isChecked }}</p>
    </div>
</template>

<script setup>
import {ref} from 'vue'

const isChecked = ref(false)

const isCheckedOk = ()=>{
    if(isChecked.value){
        alert('チェックされました！')
    }else{
        alert('チェックが外されました！')
    }
}
</script>