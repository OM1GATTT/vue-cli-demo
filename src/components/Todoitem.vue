<template>
    <RouterLink :to="{ name: 'item-details', params: { id: item.id } }">
        <div class="chunk">
            <h2>{{ item.title }}</h2>
            <img :src="'/src/assets/img/' + item.logo" alt="">
            <!-- <p v-if="item.finished">已结束</p> -->
        </div>
    </RouterLink>
</template>

<script setup>
defineProps({
    item: {
        type: Object,
        required: true,
    }
})

</script>

<style scoped>
img {
    width: 120px;
}

.chunk {
    width: 160px;
    height: 220px;
    border: 2px solid #000;
    margin-top: 20px;
    margin-bottom: 10px;
    margin-left: 20px;
    border-radius: 20px;
    text-align: center;
}
</style>