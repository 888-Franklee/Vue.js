<template>
        <h3>クラスリスト：</h3>
        <div v-for="(classGroup,calssIndex) in calssList" :key="calssIndex">
            <h4 >クラス{{ calssIndex + 1 }}：</h4>
            <ul>
                <li v-for="(student, studentIndex) in classGroup" :key="`${classIndex}-${studentIndex}`">{{ student }}</li>
            </ul>
        </div>
</template>

<script setup>
const calssList=[
    ["織田","豊臣","秀吉"],
    ["武田","上杉","毛利"],
    ["黒田","勝家","明智"],
]
</script>