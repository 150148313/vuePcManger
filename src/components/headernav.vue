<template>
  <el-row class="headernav">
    <el-col :span="4">
      <span>微商订货分销</span>
    </el-col>
    <el-col :span="12">
      <el-row>
        <el-col :span="2" class="nav" @click="$router.push('/index')">
          <i class="icon iconfont icon-tubiaozhizuomoban" @click="$router.push('/index')"></i>
          <div @click="$router.push('/index')">首页</div>
        </el-col>
        <el-col :span="2" class="nav">
          <i class="icon iconfont icon-gaikuang"></i>
          <div>概况</div>
        </el-col>
        <el-col :span="2" class="nav">
          <i class="icon iconfont icon-shangpin"></i>
          <div>商品</div>
        </el-col>
        <el-col :span="2" class="nav">
          <i class="icon iconfont icon-dianpu"></i>
          <div>店铺</div>
        </el-col>
        <el-col :span="2" class="nav">
          <i class="icon iconfont icon-icon-"></i>
          <div>订单</div>
        </el-col>
        <el-col :span="2" class="nav">
          <i class="icon iconfont icon-weixin"></i>
          <div>微商</div>
        </el-col>
        <el-col :span="2" class="nav">
          <i class="icon iconfont icon-liwu"></i>
          <div>营销</div>
        </el-col>
        <el-col :span="2" class="nav">
          <i class="icon iconfont icon-Reportformbaobiao"></i>
          <div>报表</div>
        </el-col>
        <el-col :span="3" class="nav">
          <i class="icon iconfont icon-yonghuguanli"></i>
          <div>用户管理</div>
        </el-col>
        <el-col :span="2" class="nav">
          <i class="icon iconfont icon-caiwu"></i>
          <div>财务</div>
        </el-col>
        <el-col :span="3" class="nav">
          <i class="icon iconfont icon-guanliyuan"></i>
          <div>管理员</div>
        </el-col>
      </el-row>
    </el-col>
     <el-col :span="1" class="nav">
       <i class="icon iconfont icon-set"></i>
       <div>设置</div>
     </el-col>

     <el-col :span="7">
       <el-row>
          <el-col :span="24" style="font-size: 12px;" class="text_right">
            <span class="noticetext">
              3N4W 2.0.4版本微商模块全站上线大升级 [4-12]
              <i class="icon-tubiaozhizuomoban1 icon iconfont" style="position: absolute;left: -40px;top: -30px"></i>
            </span>
          </el-col>
       </el-row>
     </el-col>
  </el-row>
</template>

<script>
/* eslint-disable indent */
  export default {}
</script>

<style lang="sass">
  .headernav
    line-height: 72px
    color: #fff
    background: #2d2f30
    font-size: 16px
    letter-spacing: 2px
    .iconfont
      font-size: 26px
    .nav
      margin: 16px 0 9px 0
      line-height: 20px
      display: block
    .nav div:active
      color: #eaffea
    .noticetext
      padding-right: 32px
      position: relative
    .noticetext::after
      position: absolute
      content: 'NEW'
      color: red
      font-size: 12px
      top: -40px
      left: -14px
</style>
