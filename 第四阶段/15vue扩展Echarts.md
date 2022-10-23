## Echarts 数据可视化

#### 一、安装 Echarts

要在项目中使用 Echarts，首先需要引入 Echarts 的依赖包。

在项目根目录中执行以下命令安装 Echarts：

```bash
npm install echarts 
or
yarn add echarts
```

#### 二、引入 Echarts

```js
// 1.在组件中引入 echarts
import * as echarts from 'echarts';
```

#### 三、Echarts 的使用

##### 1、初始化 Echarts 实例

首先，先在 template 中创建一个用于绘制图表的 DOM 节点，并设置好宽高：

```vue
 <div id="dataArea" class="dataArea">

    </div>



.dataArea{
  width: 100%;
  height: 500px;
}
```

基于准备好的原生 DOM 节点对象，初始化 Echarts 实例：

```js
export default {
    data() {
    return {
      option : {
        yAxis: {
          type: 'category',
          data: ['Mon', 'Tue', 'Wed', 'Thu', 'Fri', 'Sat', 'Sun']
        },
        xAxis: {
          type: 'value'
        },
        series: [
          {
            data: [120, 200, 150, 80, 70, 110, 130],
            type: 'bar',
            showBackground: true,
            backgroundStyle: {
              color: 'rgba(180, 180, 180, 0.2)'
            }
          }
        ]
      }

    }
  },
      mounted() {
         //获取各项类型的数量
    this.getMovieCateCount()
    //dom操作 加载 绘图到指定区域
    let myChart = echarts.init(document.getElementById('dataArea'));
   //加载数据配置项
    this.option && myChart.setOption(this.option);
  }
    }
}
```

##### 2、设置数据

在 data 中设置需要绘制的数据：

```js
 
 created() {
    this.option.yAxis.data = this.categoryList
  }
```



### 案例

```js

<template>
  <el-card>
    <div slot="header">后台数据统计</div>
    {{categoryList}}
    <div id="dataArea" class="dataArea">

    </div>
  </el-card>
</template>

<script>
import * as echarts from "echarts";
import {mapState} from "vuex"
export default {
  name: "IndexView",
  data() {
    return {
      option : {
        yAxis: {
          type: 'category',
          data: ['Mon', 'Tue', 'Wed', 'Thu', 'Fri', 'Sat', 'Sun']
        },
        xAxis: {
          type: 'value'
        },
        series: [
          {
            data: [120, 200, 150, 80, 70, 110, 130],
            type: 'bar',
            showBackground: true,
            backgroundStyle: {
              color: 'rgba(180, 180, 180, 0.2)'
            }
          }
        ]
      }

    }
  },
  computed: {
    ...mapState(["categoryList"])
  },
  watch: {},
  methods: {
    async getMovieCateCount(){
      let {data} = await this.axios.post("/api/getCharts")
      if (data.status){
        console.log(data.data)
        this.option.series[0].data = data.data
        this.initChart()
      }
    },
    initChart(){
      //dom操作 加载 绘图到指定区域
      let myChart = echarts.init(document.getElementById('dataArea'));
      //加载数据配置项
      this.option && myChart.setOption(this.option);
    }
  },
  components: {},
  created() {
    this.option.yAxis.data = this.categoryList
  },mounted() {
    //获取各项类型的数量
    this.getMovieCateCount()
  }
}
</script>

<style scoped lang="scss">
.dataArea{
  width: 100%;
  height: 500px;
}
</style>
```

