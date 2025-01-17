<script setup>
import { ref, computed } from 'vue'

const list =ref([1,2,3,4,5,6,7,8])

const computedList = computed(()=>{
    return list.value.filter(item=>item>2)
})

setTimeout(() => {
    list.value.push(9,10,11)
}, 10);
</script>

<template>
    <div>
        元のデータ：{{ list }}
    </div>
    <div>
        更新後のデータ：{{ computedList }}
    </div>
</template>