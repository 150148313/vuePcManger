<template>
    <div class="content">
      <el-row class="content_head text_left">
        <el-col :span="24">
          <span class="span">全部订单</span>
          <p>导出订单：导出的订单内容为当前搜索条件下的集合，一次最多导出100条结果。</p>
        </el-col>
         <el-col :span="24">
           <el-row class="form">
             <el-form ref="form" :model="form" label-width="50px" label-position="top"  size="mini">
               <el-row>
                 <el-col :span="8">
                   <el-row>
                     <el-col :span="6">
                       <el-form-item label="下单时间">
                         <el-date-picker
                           style="width: 96%;"
                           v-model="form.starttime"
                           type="date"
                           placeholder="开始时间" size="mini" prefix-icon="icon" @change="sttiemtbt">
                         </el-date-picker>
                       </el-form-item>
                     </el-col>
                     <el-col :span="6">
                       <el-form-item label="活动名称"  class="textout mright">
                         <el-date-picker
                           style="width: 96%;"
                           v-model="form.endtime"
                           type="date"
                           placeholder="结束时间" size="mini" prefix-icon="icon" @change="endtiemtbt">
                         </el-date-picker>
                       </el-form-item>
                     </el-col>
                     <el-col :span="6" class="">
                       <el-form-item label="订单状态" class="mright">
                         <el-select v-model="form.orderst" placeholder="请选择" @visible-change="orderbt">
                           <el-option
                             v-for="item in order_options"
                             :key="item.value"
                             :label="item.label"
                             :value="item.value">
                           </el-option>
                         </el-select>
                         <i class="icon iconfont icon-xiala_down" :class="{active: form.Ispull.indexOf(0) !== -1 }"></i>
                       </el-form-item>
                     </el-col>
                     <el-col :span="6" class="">
                       <el-form-item label="支付状态" class="mright">
                         <el-select v-model="form.payst" placeholder="请选择" @visible-change="paybt">
                           <el-option
                             v-for="item in pay_options"
                             :key="item.value"
                             :label="item.label"
                             :value="item.value">
                           </el-option>
                         </el-select>
                         <i class="icon iconfont icon-xiala_down" :class="{active: form.Ispull.indexOf(1) !== -1 }"></i>
                       </el-form-item>
                     </el-col>
                   </el-row>
                 </el-col>
                 <el-col :span="13">
                   <el-row>
                     <el-col :span="3">
                       <el-form-item label="关键字">
                         <el-input v-model="form.orderid" placeholder="订单ID"></el-input>
                       </el-form-item>
                     </el-col>
                     <el-col :span="4">
                       <el-form-item label="订单编号" class="textout">
                         <el-input v-model="form.ordernum" placeholder="订单编号"></el-input>
                       </el-form-item>
                     </el-col>
                     <el-col :span="3">
                       <el-form-item label="订单编号" class="textout">
                         <el-input v-model="form.buyerid" placeholder="买家ID"></el-input>
                       </el-form-item>
                     </el-col>
                     <el-col :span="4">
                       <el-form-item label="订单编号" class="textout">
                         <el-input v-model="form.buyername" placeholder="买家昵称"></el-input>
                       </el-form-item>
                     </el-col>
                     <el-col :span="3">
                       <el-form-item label="订单编号" class="textout">
                         <el-input v-model="form.shopid" placeholder="商品ID"></el-input>
                       </el-form-item>
                     </el-col>
                     <el-col :span="7">
                       <el-form-item label="订单编号" class="textout">
                         <el-input v-model="form.shoptitle" placeholder="商品标题"></el-input>
                       </el-form-item>
                     </el-col>
                   </el-row>
                 </el-col>
                  <el-col :span="3" style="margin-top: 30px;">
                    <i @click="searchebt" class="icon iconfont icon-sousuo" style="font-size: 20px;font-weight: 600;color: #bbbbbb;"></i>
                    <strong @click="resetbt" style="color: #bbbbbb; padding-left: 5px;">重置</strong>
                  </el-col>
               </el-row>
             </el-form>
           </el-row>
         </el-col>
      </el-row>
    </div>
</template>

<script>
/* eslint-disable indent */
  export default {
    data () {
      return {
        form: {
          starttime: '', // 开始
          endtime: '', // 结束
          orderst: '', // 订单状态
          payst: '', // 支付状态
          orderid: '', // 订单ID
          ordernum: '', // 订单编号
          buyername: '', // 买家昵称
          shopid: '', // 商品ID
          buyerid: '', // 买家ID
          shoptitle: '', // 商品标题
          Ispull: [] // 是否下拉
        },
        order_options: [{
          value: '选项1',
          label: '未发货'
        }, {
          value: '选项2',
          label: '运输中'
        }, {
          value: '选项3',
          label: '已退货'
        }, {
          value: '选项4',
          label: '已完成'
        }, {
          value: '选项5',
          label: '丢失'
        }],
        pay_options: [{
          value: '选项1',
          label: '已付款'
        }, {
          value: '选项2',
          label: '未付款'
        }, {
          value: '选项3',
          label: '已结算'
        }]
      }
    },
    prop: [],
    methods: {
      sttiemtbt (e) { // 开始时间
        if (e > this.form.endtime && this.form.endtime !== '') {
          this.$alert('请正确选择日期')
          this.form.starttime = ''
        }
      },
      endtiemtbt (e) { // 结束时间
        if (e < this.form.starttime) {
          this.$alert('请正确选择日期')
          this.form.endtime = ''
        }
      },
      orderbt (e) { // 订单状态
        if (e) {
          this.form.Ispull.push(0)
        } else {
          this.form.Ispull.splice(this.form.Ispull.indexOf(0), 1)
        }
      },
      paybt (e) { // 支付状态
        if (e) {
          this.form.Ispull.push(1)
        } else {
          this.form.Ispull.splice(this.form.Ispull.indexOf(1), 1)
        }
      },
      resetbt () { // 重置
        for (var v in this.form) {
          v !== 'Ispull' ? this.form[v] = '' : this.form.Ispull = []
        }
      },
      searchebt () {
        this.$alert('暂未开放')
      }
    }
  }
</script>

<style lang="sass">
  .content
    font-size: 14px
    margin-right: 15px
    .content_head
      background: #fff
      padding: 10px
      border-radius: 5px
      line-height: 26px
      .span
        font-size: 16px
        color: #000
        padding-left: 5px
        border-left: 3px solid #00a1e9
      p
        font-size: 14px
        color: #b6b6b6
      .form
        .el-form--label-top .el-form-item__label
          padding: 0
        input
          width: 94%
        .textout .el-form-item__label
          color: #fff
        .icon-xiala_down
          position: absolute
          top: 1px
          right: 12px
          font-size: 20px
          font-weight: 600
          color: #97a4a9
          transition: 0.2s all linear
        .icon-xiala_down.active
          transform: rotate(-180deg)
        .el-input__inner
          padding-left: 5px
        .el-input--prefix .el-input__inner
          padding: 0
          padding-left: 8px
        .el-icon-arrow-up:before
          content: ''
</style>
