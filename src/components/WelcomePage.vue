<template>
  <div class="content-page">
    <div class="content-nav">
      <el-breadcrumb class="breadcrumb" separator="/">
        <el-breadcrumb-item>后台主页</el-breadcrumb-item>
      </el-breadcrumb>
    </div>
    <div class="content-main clearfix">
      <div class="notice">
        <div class="l">二手书后台管理</div>
      </div>
      <div class="header clearfix">
        <el-card class="box-card card-red">
          <router-link class="link-color" :to="{ path: '/dashboard/order' }">
            <h1>{{ infoData.orderToDelivery }}</h1>
            <div class="text item">待发货订单</div>
          </router-link>
        </el-card>
        <el-card class="box-card card-green">
          <router-link class="link-color" :to="{ path: '/dashboard/goods' }">
            <h1>{{ infoData.goodsOnsale }}</h1>
            <div class="text item">上架中的商品</div>
          </router-link>
        </el-card>
        <el-card class="box-card card-black">
          <router-link class="link-color" :to="{ path: '/dashboard/user' }">
            <h1>{{ infoData.user }}</h1>
            <div class="text item">总用户数</div>
          </router-link>
        </el-card>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      infoData: {},
      mainInfo: {},
      loginInfo: null,
      username: '',
      label: '',
      userData: [],
      newData: [],
      oldData: [],
      related_pop: false,
      resetVision: true
    }
  },
  methods: {
    callback() {
      this.resetVision = false
    },
    getInfo() {
      this.axios.get('index').then(response => {
        this.infoData = response.data.data
      })
    }
  },
  mounted() {
    this.getInfo()
  },

  filters: {
    numFilter(value) {
      if (value) {
        let realVal = Number(value).toFixed(2)
        return Number(realVal)
      }
      return 0
    }
  }
}
</script>

<style scoped>
.notice {
  width: 100%;
  height: 60px;
  padding: 30px;
  -webkit-box-sizing: border-box;
  -moz-box-sizing: border-box;
  box-sizing: border-box;
  background: #ffecd5;
  margin-bottom: 20px;
  font-size: 16px;
  border-radius: 6px;
  display: flex;
  justify-content: space-between;
  align-items: center;
}
.github {
  width: 100%;
  height: 60px;
  padding: 30px;
  -webkit-box-sizing: border-box;
  -moz-box-sizing: border-box;
  box-sizing: border-box;
  background: #f8f8f8;
  margin-bottom: 20px;
  font-size: 16px;
  border-radius: 6px;
  display: flex;
  justify-content: flex-start;
  align-items: center;
}
.notice .r {
  display: flex;
  justify-content: space-between;
  align-items: center;
}
.github a {
  margin-right: 20px;
}
.count {
  background: #fff;
  padding: 10px;
}
.float-right {
  float: right;
}
.tips {
  color: #8c939d;
  font-size: 13px;
}

.text {
  font-size: 14px;
}

.item {
  padding: 10px 0;
}

.clearfix:before,
.clearfix:after {
  display: table;
  content: '';
}

.clearfix:after {
  clear: both;
}
.tab-content {
  margin-bottom: 20px;
}
.box-card {
  width: 32%;
  float: left;
  margin: 0 20px 14px 0;
}

.box-card:last-child {
  margin-right: 0px;
}

.box-card .link-color {
  color: #fff;
}

.box-card:last-child {
  margin-right: 0;
}

.box-card2 {
  width: 32%;
  float: left;
  margin-right: 17px;
}

.box-card2:last-child {
  margin-right: 0;
}

.header {
  margin-bottom: 30px;
}

.line {
  margin: 20px 0;
  border-top: 1px solid #d1dbe5;
}

.card-red {
  background: #e64242;
  border: none;
  color: #fff;
}

.card-blue {
  background: #4db3ff;
  border: none;
  color: #fff;
}
.card-green {
  background: #11b95c;
  border: none;
  color: #fff;
}
.card-black {
  background: #1f2d3d;
  border: none;
  color: #fff;
}
.card-gray {
  background: #d1dbe5;
  border: none;
}
.card-gray a {
  color: #1f2d3d;
}
.card-yellow {
  background: #f8dd66;
  border: none;
  color: #111111;
}

.card-yellow .link-color {
  color: #111111;
}
</style>
