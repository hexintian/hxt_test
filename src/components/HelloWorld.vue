<!--
 * @Author: liuyixue
 * @Date: 2019-07-01 09:56:18
 * @LastEditors: liuyixue
 * @LastEditTime: 2020-05-18 15:26:54
 * @Description: file content
 -->
<template>
  <div class="hello">
    <Card :bordered="false">
      <p style="font-size:20px">在线教学运行基本平稳，共运行课程{{num}}门，活跃教师{{num}}人，活跃学生{{num}}人。其中学习空间每日运行课程平均{{num}}门，每日活跃教师平均{{num}}人，每日活跃学生平均{{num}}人；雨课堂每日运行课程平均{{num}}门，每日活跃教师平均{{num}}人，每日活跃学生平均{{num}}人。</p>
    </Card>
    <Row style="margin:20px;" type="flex" justify="space-between">
      <Button style="background-color:#fb6e52;" @click="jumptoYxkc" id="yxkc">运行课程<div>{{23}}</div></Button>
      <Button style="background-color:#ffc655;" @click="jumptoHyjs" id="hyjs">活跃教师<div>{{23}}</div></Button>
      <Button style="background-color:#2dc7e9;" @click="jumptoHyxs" id="hyxs">活跃学生<div>{{23}}</div></Button>
      <Button style="background-color:#3cd7b8;" @click="jumptoHybj" id="hybj">活跃班级<div>{{23}}</div></Button>
      <Button style="background-color:#f6b37f;" @click="jumptoJxhd" id="jxhd">教学互动<div>{{23}}</div></Button>
      <Button style="background-color:#8f9ae9;" @click="jumptoJxzy" id="jxzy">教学资源<div>{{23}}</div></Button>

      <!-- <Button style="background-color:#fb6e52;" to="./yxkc">运行课程<div>{{55}}</div></Button> -->

    </Row>
    <Card :bordered="false">
      <div class="cardTitle"><Icon type="ios-square" />各院系运行课程</div>
      <Row>
        <Col span="12">
          <p>{{strings}}时段内运行课程排行前列的学院统计如图所示，其中运行量最高的学院为{{strings}}学院、{{strings}}学院、{{strings}}学院、{{strings}}学院和{{strings}}学院。</p>
        </Col>
        <Col span="12">
          <div id="map" style="height:300px"></div>
        </Col>
      </Row>
    </Card>
    <Card :bordered="false">
      <div class="cardTitle"><Icon type="ios-square" />教学互动</div>
      <Row>
        <Col span="12">
          <div id="map1" style="height:300px"></div>
        </Col>
        <Col span="12">
          <p>{{strings}}时段内教学过程中平均每日互动数量为{{num}}次，具体教学互动情况如图所示。</p>
        </Col>
        
      </Row>
    </Card>
    <Card :bordered="false">
      <div class="cardTitle"><Icon type="ios-square" />教学资源</div>
      <Row>
        <Col span="12">
          <p>{{strings}}时段内各课程教学资源上传数量如图所示，其中教学资源上传数量最多的课程为{{strings}}，{{strings}}，     ，{{strings}}和{{strings}}。 </p>
        </Col>
        <Col span="12">
          <div id="map2" style="height:300px"></div>
        </Col>
      </Row>
    </Card>
    <Card :bordered="false">
      <div class="cardTitle"><Icon type="ios-square" />到课率</div>
      <Row>
        <Col span="12">
          <div id="map3" style="height:300px"></div>
        </Col>
        <Col span="12">
          <p>{{strings}}时段内教学过程中平均到课率为{{num}}，具体到课率统计如图所示。 </p>
        </Col>
      </Row>
    </Card>
    <Card :bordered="false">
      <div class="cardTitle"><Icon type="ios-square" />最受欢迎课程</div>
      <Row>
        <Col span="12">
          <p>{{strings}}时段内最受学生们欢迎的课程为{{strings}}、{{strings}}、{{strings}}、{{strings}}和{{strings}}。参与学生人数较多的课程与其参与人次如图所示。 </p>
        </Col>
        <Col span="12">
          <div id="map4" style="height:300px"></div>
        </Col>
      </Row>
    </Card>
    <Card :bordered="false">
      <div class="cardTitle"><Icon type="ios-square" />学习空间（学习通）</div>
      <p>学习空间（学习通）共运行课程{{num}}门，平均每日运行课程{{num}}门，活跃教师{{num}}人，平均每日活跃教师{{num}}人，活跃学生{{num}}人，平均每日活跃学生{{num}}人。详细情况如下表所示: </p>
      <!-- <div style="width:80%"> -->
        <Row type="flex" justify="center">
          <Col span="4"></Col>
          <Col span="16">
            <Table border stripe :columns="XxkjTable.columns1" :data="XxkjTable.data1"/>
          </Col>
          <Col span="4"></Col>
          <!-- <Page
            :total="total"
            ref="pager"
            :page-size="limit"
            :page-size-opts="[10,30,50]"
            show-elevator
            show-total
            show-sizer
            placement="top"
            @on-change="changePage"
            @on-page-size-change="changePageSize"
          ></Page> -->
        </Row>
      <!-- </div> -->
    </Card>
    <Card :bordered="false">
      <div class="cardTitle"><Icon type="ios-square" />雨课堂</div>
      <p>雨课堂共运行课程{{num}}门，平均每日运行课程{{num}}门，活跃教师{{num}}人，平均每日活跃教师{{num}}人，活跃学生{{num}}人，平均每日活跃学生{{num}}人。详细情况如下表所示: </p>
        <Row type="flex" justify="center">
          <Col span="4"></Col>
          <Col span="16">
        <Table border stripe  :columns="YktTable.columns1" :data="YktTable.data1"/>
        </Col>
          <Col span="4"></Col>
          <!-- <Page
            :total="total"
            ref="pager"
            :page-size="limit"
            :page-size-opts="[10,30,50]"
            show-elevator
            show-total
            show-sizer
            placement="top"
            @on-change="changePage"
            @on-page-size-change="changePageSize"
          ></Page> -->
        </Row>
      </Card>
    <Card :bordered="false">
      <div class="cardTitle"><Icon type="ios-square" />运行监测</div>
      <p>根据本周运行监测：</p>
      <div class="p_inAll">
        <p>1.经监测，各个技术支持群本周出现个别用户咨询问题，集中在腾讯课堂摄像头显示、雨课堂统计到课率、大学MOOC的使用问题、网络缴费问题、雨课堂留学生登录问题等，中心均已协调解决。</p>
        <p>2.因疫情期间数据接口调整，导致学校中间库数据同步不及时。雨课堂本周修复了数据接口同步的问题。</p>
        <p>3.本周有老师在备课时反馈超星直播客户端对上传加载的图片格式判断不正确，不能很好的适配。超星给出解决方案：3月30日上午完成了直播客户端的最新更新：优化了加载图片时，对图片格式的判断；同时也修改了屏幕共享直播时，自动切换到图片的问题。</p>
      </div>
      
    </Card>
    <Row type="flex" justify="center">
      <Col span="10"></Col>
      <Col span="4">
        <Button style="background-color:#a40000;width:200px" @click="exportReport">点击导出简报</Button>
      </Col>
      <Col span="10"></Col>
    </Row>
  </div>
</template>

<script>
import { tbXxkjList,tbYktList } from '../js/tables'

export default {
  name: 'HelloWorld',
  data () {
    // const checkInfoList = checkInfoListFunc(this)
    // const pageSize = this.limit
    // const pageOffset = this.offset
    // const total = checkInfoList.data1.length
    return {
      num: 99,
      strings: 'here',
      msg: 'Welcome to Your Vue.js App',
      total: 7,
      // limit: parseInt(pageSize) || 10, // 每页条数
      // offset: parseInt(pageOffset) || 0, // 每页的查询索引
      XxkjTable:{
        columns1: tbXxkjList.columns1,
        data1: tbXxkjList.data1
      },
      YktTable:{
        columns1: tbYktList.columns1,
        data1: tbYktList.data1
      }
      
    }
  },
  mounted() {
    this.echartsGeo()
  },
  methods: {
    jumptoYxkc() {
      this.$router.push({
        path: '/yxkc'
      })
    },
    jumptoHyjs() {
      this.$router.push({
        path: '/hyjs'
      })
    },
    jumptoHyxs() {
      this.$router.push({
        path: '/hyxs'
      })
    },
    jumptoHybj() {
      this.$router.push({
        path: '/hybj'
      })
    },
    jumptoJxhd() {
      this.$router.push({
        path: '/jxhd'
      })
    },
    jumptoJxzy() {
      this.$router.push({
        path: '/jxzy'
      })
    },
    echartsGeo() {
      let echarts = require('echarts')
      let myChart = echarts.init(document.getElementById('map'))
      let myChart1 = echarts.init(document.getElementById('map1'))
      let myChart2 = echarts.init(document.getElementById('map2'))
      let myChart3 = echarts.init(document.getElementById('map3'))
      let myChart4 = echarts.init(document.getElementById('map4'))


      let option = {
        dataset: {
          source: [
            [ 'amount', 'product'],
            [ 58212, 'Matcha Latte'],
            [ 78254, 'Milk Tea'],
            [ 41032, 'Cheese Cocoa'],
            [ 12755, 'Cheese Brownie'],
            [ 20145, 'Matcha Cocoa'],
            [ 79146, 'Tea'],
            [ 91852, 'Orange Juice'],
            [ 101852, 'Lemon Juice'],
            [ 20112, 'Walnut Brownie']
          ]
        },
        grid: {containLabel: true},
        xAxis: {name: 'amount'},
        yAxis: {type: 'category'},
        visualMap: {
          // 视觉效果数值以横坐标amount为基准
          orient: 'horizontal',
          left: 'center',
          min: 10000,
          max: 100000,
          text: ['High Score', 'Low Score'],
          // Map the score column to color
          dimension: 0,
          inRange: {
              color: ['#D7DA8B', '#E15457']
          }
        },
        series: [
          {
            type: 'bar',
            encode: {
              // Map the "amount" column to X axis.
              x: 'amount',
              // Map the "product" column to Y axis
              y: 'product'
            }
          }
        ]
      };

      let option1 = {
        xAxis: {
          type: 'category',
          boundaryGap: false
        },
        yAxis: {
          type: 'value',
          boundaryGap: [0, '30%']
        },
        visualMap: {
          type: 'piecewise',
          show: false,
          dimension: 0,
          seriesIndex: 0,
          pieces: [{
            gt: 1,
            lt: 3,
            color: 'rgba(0, 180, 0, 0.5)'
          }, {
            gt: 5,
            lt: 7,
            color: 'rgba(0, 180, 0, 0.5)'
          }]
        },
        series: [
          {
            type: 'line',
            smooth: 0.6,
            symbol: 'none',
            lineStyle: {
              color: 'green',
              width: 5
            },
            markLine: {
              symbol: ['none', 'none'],
              label: {show: false},
              data: [
                {xAxis: 1},
                {xAxis: 3},
                {xAxis: 5},
                {xAxis: 7}
              ]
            },
            areaStyle: {},
            data: [
              ['2019-10-10', 200],
              ['2019-10-11', 400],
              ['2019-10-12', 650],
              ['2019-10-13', 500],
              ['2019-10-14', 250],
              ['2019-10-15', 300],
              ['2019-10-16', 450],
              ['2019-10-17', 300],
              ['2019-10-18', 100]
            ]
          }
        ]
      };
      let option2 = {
        color: ['#3398DB'],
        xAxis: {
            type: 'category',
            data: ['Mon', 'Tue', 'Wed', 'Thu', 'Fri', 'Sat', 'Sun']
        },
        yAxis: {
            type: 'value'
        },
        series: [{
            data: [120, 200, 150, 80, 70, 110, 130],
            type: 'bar'
        }]
      };
      let option3 = {
        xAxis: {
            type: 'category',
            data: ['Mon', 'Tue', 'Wed', 'Thu', 'Fri', 'Sat', 'Sun']
        },
        yAxis: {
            type: 'value'
        },
        series: [{
            data: [120, 200, 150, 80, 70, 110, 130],
            type: 'line',
            areaStyle: {}
        }]
      };
      myChart.setOption(option)
      myChart1.setOption(option1)
      myChart2.setOption(option2)
      myChart3.setOption(option3)
      myChart4.setOption(option2)

    },
    changePage (d) {
        let self = this
        self.offset = self.limit * (d - 1)
        self.getList()
      },
    changePageSize (d) {
      let self = this
      self.limit = d
      if (self.$refs['pager'].currentPage === 1) {
        self.getList()
      }
    },
    exportReport() {
      alert('还未实现')
    }
  },
}
</script>
<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
/* 首个卡片字号不同，略大 */
.ivu-card{
  margin:20px;
  font-size: 18px;
}

/* 首行缩进 */
p{ 
  text-indent:2em;
  line-height: 2;
}
.p_inAll p{
  text-indent:0;
  margin-left:2em;
  margin-right: 1em;
}
/* 修改按钮格式 */
[type=button]{
  width: 160px;
  height: 65px;
  font-size: 20px;
  font-weight: bold;
  color: #fff;
}
.cardTitle{
  margin-bottom: 10px;
  font-size: 24px;
  font-weight: bold;
  color: #255aaa;
}
.ivu-icon{
  color: #255aaa;
  line-height: 0;
  margin-right: 10px;
  vertical-align: 0;
}

</style>
