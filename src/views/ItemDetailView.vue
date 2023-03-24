<template>
    <div class="chunk">
        <div style="flex:2; margin:auto">
            <img :src="'/src/assets/img/' + item.logo" alt="">
        </div>
        <div style="flex:4; text-align: center;">
            <h2>{{ item.title }}</h2>
            <div class="date">{{ item.date }}</div>
        </div>
    </div>
</template>

<script setup>
import { onBeforeMount, ref, onMounted } from 'vue'
import ItemService from '@/services/ItemService.js'

const props = defineProps({
    id: {
        type: String,
        required: true,
    },
})
let item = ref(null);

onBeforeMount(() => {
    ItemService.getItem(props.id)
        .then((res) => {
            item.value = res.data;
            console.log(item);
        })
        .catch((error) => {
            console.log(error)
        })
})
</script>

<style scoped>
.chunk {
    width: 330px;
    height: 180px;
    border: 1px solid black;
    border-radius: 20px;
    margin: 0 auto;
    margin-top: 20px;
    display: flex;
}

img {
    width: 130px;
}

.date {
    padding: 20px 20px;
}
</style>