<template>
  <el-container>
    <el-container>
      <el-header>
        <!-- Header content -->
        <el-breadcrumb separator-class="el-icon-arrow-right">
          <el-breadcrumb-item :to="{ path: '/friday/home/index' }">首页</el-breadcrumb-item>
          <el-breadcrumb-item> </el-breadcrumb-item>
        </el-breadcrumb>
      </el-header>
      <el-main>
        <!-- Main content -->
        <!-- 走马灯 -->
        <el-carousel indicator-position="outside">
          <el-carousel-item v-for="item in 4" :key="item">
            <h3>{{ item }}</h3>
          </el-carousel-item>
        </el-carousel>

        <el-row :gutter="50" id="footer">
          <el-col :span="10">
            <el-row :gutter="15">
              <el-col :span="8">
                  <el-card shadow="always">
                    <el-row>
                      <el-col> <p>托管集群：</p> </el-col>
                    </el-row>
                    <el-row type="flex" justify="center">
                      <el-col :span="8"> <el-link class="highlight-char" @click="showClusterView">{{ cluster_cnt }}</el-link> </el-col>
                    </el-row>
                  </el-card>
              </el-col>
              <el-col :span="8">
                  <el-card shadow="always">
                    <el-row>
                      <el-col> <p>运行任务：</p> </el-col>
                    </el-row>
                    <el-row type="flex" justify="center">
                      <el-col :span="8"> <el-link class="highlight-char" @click="showTaskView">{{ task_cnt }}</el-link> </el-col>
                    </el-row>
                  </el-card>
              </el-col>
              <el-col :span="8">
                  <el-card shadow="always">
                    <el-row>
                      <el-col> <p>镜像数量：</p> </el-col>
                    </el-row>
                    <el-row type="flex" justify="center">
                      <el-col :span="8"> <el-link class="highlight-char" @click="showImageView">{{ image_cnt }}</el-link> </el-col>
                    </el-row>
                  </el-card>
              </el-col>
            </el-row>
          </el-col>
          <!-- 处理任务数量曲线图表 -->
          <el-col :span="13">
            <ve-line :data="chartData"></ve-line>
          </el-col>
        </el-row>
      </el-main>
    </el-container>
  </el-container>
</template>
<script>
  export default {
	name:'cluster_view',
	  data(){
		  return{
        cluster_cnt: 0,
        task_cnt: 0,
        image_cnt: 0,
        chartData: {
          columns: ['date', '执行任务数', '集群数量', '镜像数量', '用户访问量'],
          rows: [
            {'date': "5-5", '执行任务数': '0', '集群数量': 1, '镜像数量': 2, '用户访问量':3},
            {'date': "5-6", '执行任务数': '0', '集群数量': 1, '镜像数量': 2, '用户访问量':2},
            {'date': "5-7", '执行任务数': '0', '集群数量': 1, '镜像数量': 2, '用户访问量':1},
            {'date': "5-8", '执行任务数': '0', '集群数量': 1, '镜像数量': 2, '用户访问量':3},
            {'date': "5-9", '执行任务数': '0', '集群数量': 1, '镜像数量': 2, '用户访问量':4},
          ]
        }
		  }
    },
    methods: {
      showClusterView(){
        this.$router.push('/friday/home/cluster_view')
      },
      showTaskView(){
        this.$router.push('/friday/home/task_view')
      },
      showImageView(){
        this.$router.push('/friday/home/image_view')
      },
    }
    }
</script>
<style type="text/css" scoped>
  .el-row {
    margin-bottom: 20px;
  }
  .el-col {
    border-radius: 4px;
  }

  .el-carousel__item h3 {
    color: #475669;
    font-size: 18px;
    opacity: 0.75;
    line-height: 300px;
    margin: 0;
  }
  .el-carousel__item:nth-child(2n) {
    background-color: #99a9bf;
  }
  .el-carousel__item:nth-child(2n+1) {
    background-color: #d3dce6;
  }

  #footer {
    margin-top: 30px;
    min-height: 400px;
  }
  .el-card {
    height: 140;
  }

  .highlight-char {
    font-size: 60px;
    font-weight: bold;
    font-family: "Helvetica Neue";
    text-align: center;
  }

  .bg-purple {
    background: #d3dce6;
  }
    .grid-content {
    border-radius: 4px;
    min-height: 250px;
  }
</style>