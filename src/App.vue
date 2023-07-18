<template>
  <Bar
    id="my-chart-id"
    :options="chartOptions"
    :data="chartData"
  />
</template>

<script setup lang="ts">
import { Bar } from 'vue-chartjs'
import { Chart as ChartJS, Title, Tooltip, Legend, BarElement, CategoryScale, LinearScale } from 'chart.js'
import { ref } from 'vue';

ChartJS.register(Title, Tooltip, Legend, BarElement, CategoryScale, LinearScale)

const CHART_COLORS = {
  red: 'rgb(255, 99, 132)',
  orange: 'rgb(255, 159, 64)',
  yellow: 'rgb(255, 205, 86)',
  green: 'rgb(75, 192, 192)',
  blue: 'rgb(54, 162, 235)',
  purple: 'rgb(153, 102, 255)',
  grey: 'rgb(201, 203, 207)'
}


const chartData = ref({
  labels: [ 'text1', 'text2', 'text3', 'text4', 'text5'],
  datasets: [
    {
      label: 'Q1',
      left: 400,
      backgroundColor: CHART_COLORS.blue,
      data: [-100, -120, -140, -150, -90],
    },
    {
      label:  'Q2',
      backgroundColor: CHART_COLORS.yellow,
      data: [200, 230, 250, 250, 250],
    },
    {
      label:  'Q3',
      backgroundColor: CHART_COLORS.red,
      data: [100, 150, 130, 100, 220],
    },
  ]
})
const chartOptions = ref({
  indexAxis: 'y',	
  plugins: {
      title: {
        display: true,
        text: 'WHERE WE ARE GOING TO LAND ?',
        align: 'start'
      },
      legend: {
        display: true,
        align: 'center'
      }
    },
	scales: {
		x: {
			ticks: {
				color: 'black',
				getLabelForValue: (value) => new Date(value)
			},
			stacked: true
		},
		y: {
			display: true,
			stacked: true,
      beginAtZero: false,
			ticks: {
				stepSize: 200,
				color: 'black'
			}
		}
	}
})
</script>

<style>
#my-chart-id {
  height: 80vh;
  width: 80vw;
}
</style>