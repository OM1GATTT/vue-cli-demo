<template>
    <div style="display: flex; justify-content:space-around;">
        <div v-for="item in items" :key="item.id">

            <Todoitem :item="item"></Todoitem>
        </div>
    </div>
</template>

<script setup>
//引入todoitem组件
import Todoitem from '../components/Todoitem.vue';

import { ref, onMounted } from 'vue';
import ItemService from '@/services/ItemService.js'

let items = ref(null)
onMounted(() => {
    ItemService.getTodoItems()
        .then((res) => {
            items.value = res.data
            console.log(items)
        })
        .catch((error) => {
            console.log(error)
        })
})



// const items = reactive([
//     {
//         id: 1,
//         title: "Vue3学习",
//         date: "2023-03-24",
//         logo: "/src/assets/img/RealWorldVue3.png",
//         finished: false
//     },
//     {
//         id: 2,
//         title: "Pinia学习",
//         date: "2023-03-24",
//         logo: "/src/assets/img/Pinia.opt.png",
//         finished: false
//     },
//     {
//         id: 3,
//         title: "Ts学习",
//         date: "2023-03-24",
//         logo: "/src/assets/img/TypeScript Friendly Vue 3.opt.png",
//         finished: true
//     },
//     {
//         id: 4,
//         title: "Vite",
//         date: "2023-03-24",
//         logo: "/src/assets/img/Vite.opt.png",
//         finished: true
//     }
// ])
</script>

<style lang="scss" scoped></style>