<script setup>
import { ref, onMounted, nextTick } from 'vue';

const items = ref([
    'https://media.istockphoto.com/id/1942690071/photo/ram-mandir-pran-pratishtha-diya-ceremony.jpg?s=1024x1024&w=is&k=20&c=G2OM6PG7d7nz_zARCY9Mrtg9ctNHYnQkJjsjsji_uyk='
    , 'https://images.unsplash.com/photo-1561032931-09034fb93094?q=80&w=1407&auto=format&fit=crop&ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D'
    , 'https://images.unsplash.com/photo-1526481280693-3bfa7568e0f3?q=80&w=1471&auto=format&fit=crop&ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D'
    , 'https://images.unsplash.com/photo-1559565779-302744980c7c?q=80&w=1470&auto=format&fit=crop&ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D'
    , 'https://images.unsplash.com/photo-1578469550956-0e16b69c6a3d?q=80&w=1406&auto=format&fit=crop&ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D'
    , 'https://images.unsplash.com/photo-1506462945848-ac8ea6f609cc?q=80&w=1472&auto=format&fit=crop&ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D'
    , 'https://plus.unsplash.com/premium_photo-1661891622579-bee76e28c304?q=80&w=1481&auto=format&fit=crop&ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D'
    , 'https://media.istockphoto.com/id/481272289/photo/el-castillo-of-chichen-itza-at-sunset-mexico.jpg?s=1024x1024&w=is&k=20&c=RJQmvHb-DmmOludKS3H5hzSlk2sIEBDt9LmG_vf2o8M='
    , 'https://images.unsplash.com/photo-1517481700215-fddbbf01b509?q=80&w=1470&auto=format&fit=crop&ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D'

])

let carousel = null;
const newItem = ref('https://d3nn873nee648n.cloudfront.net/900x600/20743/300-SM1072724.jpg')

function addNewItem() {
    items.value.push(newItem.value);
    carousel.destroy();
    nextTick(() => {
        carousel = new Flickity('#carousel', {});
    })
}

onMounted(() => {
    carousel = new Flickity('#carousel', {});
})



</script>

<template>
    <div class="my-10 mx-auto flex justify-center ">
        <input class="py-2 px-4 border-2" type="text" v-model="newItem">
        <button @click="addNewItem()" class="ml-2 bg-blue-500 hover:bg-blue-700 text-white font-bold py-2 px-4">
            Add New Item
        </button>
    </div>

    <div class="mx-auto items" id="carousel">
        <div class="item" v-for="(item, index) in items" :key="item" :style="`background-image: url(${item})`">
            {{ index + 1 }}

        </div>
    </div>
</template>

<style scoped>
.items {
    margin: 30px auto;
    width: 600px;
    height: 400px;
}

.item {
    width: 100%;
    height: 100%;
    background-size: contain;
}
</style>
