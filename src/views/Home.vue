<template>
  <div class="home">
    <img alt="Vue logo" src="../assets/logo.png" />
    <div id="main" style="width: 100%; height: 400px"></div>
  </div>
</template>

<script>
// @ is an alias to /src
import * as echarts from "echarts";
import { onMounted } from "vue";

export default {
  name: "Home",
  setup() {
    const echartInit = () => {
      var myChart = echarts.init(document.getElementById("main"));
      // 指定图表的配置项和数据
      var option = {
        title: {
          text: "ECharts 入门示例",
        },
        tooltip: {},
        legend: {
          data: ["销量"],
        },
        xAxis: {
          data: ["衬衫", "羊毛衫", "雪纺衫", "裤子", "高跟鞋", "袜子"],
        },
        yAxis: {},
        series: [
          {
            name: "销量",
            type: "bar",
            data: [5, 20, 36, 10, 10, 20],
          },
        ],
      };
      // 使用刚指定的配置项和数据显示图表。
      myChart.setOption(option);
    };
    // 挂载钩子
    onMounted(() => {
      echartInit();
    });

    return {
      echartInit,
    };
  },
};
</script>
