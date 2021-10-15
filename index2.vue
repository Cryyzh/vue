<template>
  <div>
    <van-nav-bar style="background-color: #495af0" title="数据统计" />

    <van-tabs @rendered="zhuzhuang(), void_zhexiang()" color="#495af0">
      <!-- 第一个界面 -->
      <van-tab title="数据统计">
        <div class="a21">
          <div>{{ weichulibaojin }}</div>
          <div>今日未处理报警数</div>
        </div>
        <!-- 报警统计栏 -->
        <div class="a22">
          <div style="">报警统计</div>
          <div class="a23">
            <div>
              <div>105</div>
              <div>今日报警数</div>
            </div>
            <div>
              <div>117</div>
              <div>未处理报警数</div>
            </div>
            <div>
              <div>123</div>
              <div>报警总数</div>
            </div>
          </div>
        </div>

        <!-- 能耗统计栏 -->
        <div class="a22">
          <div style="">能耗统计</div>
          <div class="a23">
            <div>
              <div>291h</div>
              <div>总运行时长</div>
            </div>
            <div>
              <div>8730kw/h</div>
              <div>总能耗</div>
            </div>
            <div>
              <div>￥10476</div>
              <div>总电费</div>
            </div>
          </div>
        </div>
        <!-- 表格栏 -->
        <div class="a24">
          最近七日电费
          <div id="zhuzhuangtu" style="width: 100%; height: 100%"></div>
        </div>
      </van-tab>
      <!-- 第二个界面 -->
      <van-tab title="数据预测">
        <div id="zhexiang" style="width: 100%; height: 280px"></div>

       
      </van-tab>
    </van-tabs>
  </div>
</template>

<script>
import * as echarts from "echarts";

export default {
  data() {
    return {
      weichulibaojin: 99,
    };
  },
  // mounted:function name() {

  //   this.zhuzhuang();
  // } ,

  methods: {
    zhuzhuang() {
      var chartDom = document.getElementById("zhuzhuangtu");
      var myChart = echarts.init(chartDom);
      var option;

      option = {
        xAxis: {
          type: "category",
          data: ["Mon", "Tue", "Wed", "Thu", "Fri", "Sat", "Sun"],
        },
        yAxis: {
          type: "value",
        },
        series: [
          {
            data: [120, 200, 150, 80, 70, 110, 130],
            type: "bar",
          },
        ],
      };

      option && myChart.setOption(option);
    },

    void_zhexiang() {
      var chartDom = document.getElementById("zhexiang");
      var myChart = echarts.init(chartDom);
      var option;

      option = {
        xAxis: {
          type: "category",
          data: ["Mon", "Tue", "Wed", "Thu", "Fri", "Sat", "Sun"],
        },
        yAxis: {
          type: "value",
        },
        series: [
          {
            data: [150, 230, 224, 218, 135, 147, 260],
            type: "line",
          },
        ],
      };

      option && myChart.setOption(option);
    },
  },
};
</script>

<style >
.a21 {
  width: 96%;
  height: 50px;
  margin: 15px auto;
  padding: 30px 0px;
  text-align: center;
  border-radius: 8px;
  background-color: #495af0;
}
.a22 {
  width: 96%;
  height: 80px;
  margin: 15px auto;
  padding: 10px 0px;
  border-radius: 8px;
  background-color: #ffffff;
}
.a23 {
  display: flex;
  margin: 10px auto;
  justify-content: space-evenly;
  text-align: center;
}
.a24 {
  width: 96%;
  height: 280px;
  margin-left: 15px;
}
</style>