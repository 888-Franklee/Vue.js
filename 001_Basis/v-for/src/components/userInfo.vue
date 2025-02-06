<template>
    <ul>
        <li v-for="(item, key) in userInfo" :key="key">
            {{ key }}：{{ item }}
        </li>
    </ul>

</template>

<script setup>
const userInfo ={
    氏名 : "織田信長",
    年齢 : 28,
    出身 : "尾張"
}
</script>