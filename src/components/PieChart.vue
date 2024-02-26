<script setup>
import { ref, onMounted } from 'vue'

const newItem = ref(16)
let chart = null;
const dataset = [300, 50, 100]

const data = {
    labels: [
        'Red',
        'Blue',
        'Yellow'
    ],
    datasets: [{
        label: 'My First Dataset',
        data: dataset,
        backgroundColor: [
            'rgb(255, 99, 132)',
            'rgb(54, 162, 235)',
            'rgb(255, 205, 86)'
        ],
        hoverOffset: 4
    }]
};

const config = {
    type: 'pie',
    data: data,
};

onMounted(() => {
    const ctx = document.getElementById('chart');
    chart = new Chart(ctx, config);
})

function updateChart() {
    dataset.push(newItem.value);
    chart.data.datasets[0].data = dataset;
    chart.update()
}
</script>

<template>
    <h2 class="text-3xl text-center font-bold my-10">Pie chart With <a
            href="https://www.chartjs.org/docs/4.4.1/getting-started/">Chartjs</a></h2>
    <div class="mx-auto w-[400px] h-[400px] bg-gray-400">
        <canvas id="chart"></canvas>
    </div>
    <div class="my-10 mx-auto flex justify-center ">
        <input type="text" v-model="newItem" class="py-2 px-4 border-4">
        <button @click=" updateChart()"
            class="ml-2 bg-blue-200 hover:bg-blue-700 text-white font-bold py-2 px-4 rounded">Add</button>
    </div>
</template>


<style lang="scss" scoped></style>