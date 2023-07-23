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
  data: [0.2, 0.3, 0.4, 0, 0.5, 0.5]
}, {
  name: 'EXPECTED',
  data: [0.35, 1.1, 1.0, 0, 1.2, 1.2]
}, {
  name: 'UNLIKELY',
  data: [0.25, 0.3, 0.35, 0, 1.0, 1.1]
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
  colors: ['#77b9e5', '#e7c81c', '#ee3f37'],
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
        const value = (val + 6.5).toString()
        return "$" + (value.includes('.') ? value : value + '.0') + "M"
      }
    },
    stacked: true,
    min: 0,
    max: 9
  },
  yaxis: {
    title: {
      text: undefined
    },
    stacked: true
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
},
dataLabels: {
  enabled: false
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
  background-color: #77b9e5;
}

.apexcharts-legend-text {
  position: absolute !important;
  margin: auto !important;
  color: white !important
}
</style>