<template>
 <div id="chart">
  <div class="toolbar">
    <button @click="selection = true" :class="{active: selection}">
      SALES
    </button>
    
    <button @click="selection = false" :class="{active: !selection}">
        PROSPECTING
    </button>
  </div>

  <div id="chart-timeline">
    <VueApexCharts type="bar" height="350" :options="chartOptions" :series="series"/>
  </div>
  </div>
</template>

<script setup lang="ts">
import VueApexCharts from "vue3-apexcharts";
import { ref } from 'vue';

const selection = ref(true)

 const series  = ref([{
  name: 'CERTAIN',
  data: [4, 5.5, 4.1,0,  3.7, 2.2]
}, {
  name: 'EXPECTED',
  data: [5.3, 3.2, 3.3,0,  5.2, 1.3]
}, {
  name: 'UNLIKELY',
  data: [1.2, 1.7, 1.1,0,  9, 1.5]
}])

const chartOptions = ref({
  annotations: {
    yaxis: [
      {
        y: '',
        strokeDashArray: 10
      }
    ]
},
  chart: {
    type: 'bar',
    stacked: true,
    
  },
  colors: ['rgb(54, 162, 235)', 'rgb(255, 205, 86)', 'rgb(255, 99, 132)'],
  plotOptions: {
    bar: {
      horizontal: true
    },
  },
  stroke: {
    width: 0,
    colors: ['#fff']
  },
  title: {
    text: 'Where Are We Goind To Land?',
    style: {
      fontSize:  '20px',
      fontWeight:  'bold'
    },
  },
  xaxis: {
    categories: ['CURRENT MO.', 'NEXT MO.', 'FOLLOWING MO.', '', 'CURRENT Q.', 'NEXT Q'],
    labels: {
                formatter: function (val) {
                  return val + "K"
                }
              }
  },
  yaxis: {
    title: {
      text: undefined
    },
  },
  fill: {
    opacity: 1
  },
  legend: {
      position: 'top',
      horizontalAlign: 'center', 
      floating: true,
      fontSize: '12px',
      fontFamily: 'Helvetica, Arial',
      fontWeight: 700,
      markers: {
          width: 90,
          height: 16,
          radius: 12,
      },
      onItemClick: {
          toggleDataSeries: false
      },
      onItemHover: {
          highlightDataSeries: false
      },
  },
  grid: {
    show: true,
    borderColor: '#90A4AE',
    strokeDashArray: 0,
    position: 'back',
    xaxis: {
        lines: {
            show: true
        }
    },   
    yaxis: {
        lines: {
            show: false
        }
    },  
    row: {
        colors: undefined,
        opacity: 1
    },  
    column: {
        colors: 'undefined',
        opacity: 0
    },  
    padding: {
        top: 10,
        right: 0,
        bottom: 0,
        left: 10
    },  
}
})

</script>

<style>
#chart {
  height: 80vh;
  width: 80vw;
  position: relative;
}

.toolbar {
  position: absolute;
  border: 2px solid #000;
  right: 0;
  z-index: 1000;
}

.apexcharts-legend {
  top: 2px !important
}
button:focus, button:focus-visible,
button {
  border-radius: 0 !important;
  border: 0 !important;
  width: 120px;
  font-size: 12px;
  outline: 0;
}

.active {
  background-color: rgb(54, 162, 235);
}

.apexcharts-legend-text {
  position: absolute !important;
  margin: auto !important;
  color: white !important
}
</style>