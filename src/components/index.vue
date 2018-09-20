<template>
  <div class="index">
    <my-Header :text="111"></my-Header>
    <el-row>
      <el-col :span="4">
        <el-row class="userinfo">
          <el-col :span="8">
            <img src="../assets/logo.png" alt="">
          </el-col>
          <el-col :span="12" style="" class="name">
             <div>刘志强</div>
             <span class="icon iconfont icon-set"></span>
             <span class="icon iconfont icon-exit"></span>
           </el-col>
           <el-col :span="24">
             <el-row>
               <el-col :span="12" class="order">
                 <span>微商订单 </span>
                 <span class="tip">2</span>
               </el-col>
               <el-col :span="12" class="order">
                 <span>商城订单 </span>
                 <span class="tip">2</span>
               </el-col>
             </el-row>
           </el-col>
        </el-row>
        <el-row class="left_nav">
          <el-col :span="24">
            <el-row class="left_nav_item">
              <div @click="opensonbt(0)">
              <el-col :span="5"  style="">
                <span class="icon iconfont icon-shangpin"></span>
              </el-col>
              <el-col :span="13" class="text_left">
                <span>商品管理</span>
              </el-col>
              <el-col :span="3" style="">
                <span class="icon iconfont" :class="[openlist.indexOf(0) !== -1 ? icon[1] : icon[0]]"></span>
              </el-col>
              </div>
            </el-row>
            <div v-if="openlist.indexOf(0) !== -1" v-for="(item, key) in list" :key="key" @click="selectsonbt(key)">
              <el-row class="left_nav_son" :class="{active: selectlist.indexOf(key) !== -1}">
                <el-col :span="5"  style="">
                  <span class="icon iconfont" :class="[selectlist.indexOf(key) !== -1 ? icon[2] : icon[3]]"></span>
                </el-col>
                <el-col :span="16" class="text_left">
                  <span>{{item.title}} {{item.value}}</span>
                </el-col>
              </el-row>
            </div>
            <el-row class="left_nav_item">
              <div @click="opensonbt(1)">
                <el-col :span="5"  style="">
                  <span class="icon iconfont icon-shangpin"></span>
                </el-col>
                <el-col :span="13" class="text_left">
                  <span>商品管理</span>
                </el-col>
                <el-col :span="3" style="">
                  <span class="icon iconfont" :class="[openlist.indexOf(1) !== -1 ? icon[1] : icon[0]]"></span>
                </el-col>
              </div>
            </el-row>
            <div v-if="openlist.indexOf(1) !== -1" v-for="(item, key2) in list" :key="key2" @click="selectsonbt(key2)">
              <el-row class="left_nav_son" :class="{active: selectlist.indexOf(key2) !== -1}">
                <el-col :span="5"  style="">
                  <span class="icon iconfont" :class="[selectlist.indexOf(key2) !== -1 ? icon[2] : icon[3]]"></span>
                </el-col>
                <el-col :span="16" class="text_left">
                  <span>{{item.title}} {{item.value}}</span>
                </el-col>
              </el-row>
            </div>
            <el-row class="left_nav_item">
              <div @click="opensonbt(2)">
                <el-col :span="5"  style="">
                  <span class="icon iconfont icon-shangpin"></span>
                </el-col>
                <el-col :span="13" class="text_left">
                  <span>商品管理</span>
                </el-col>
                <el-col :span="3" style="">
                  <span class="icon iconfont" :class="[openlist.indexOf(2) !== -1 ? icon[1] : icon[0]]"></span>
                </el-col>
              </div>
            </el-row>
            <div v-if="openlist.indexOf(2) !== -1" v-for="(item, key1) in list" :key="key1" @click="selectsonbt(key1)">
              <el-row class="left_nav_son" :class="{active: selectlist.indexOf(key1) !== -1}">
                <el-col :span="5"  style="">
                  <span class="icon iconfont" :class="[selectlist.indexOf(key1) !== -1 ? icon[2] : icon[3]]"></span>
                </el-col>
                <el-col :span="16" class="text_left">
                  <span>{{item.title}} {{item.value}}</span>
                </el-col>
              </el-row>
            </div>
          </el-col>
        </el-row>
      </el-col>
      <el-col :span="20">
        <el-row class="mian_content">
          <my-Content></my-Content>
           <el-col :span="24" class="text_left">
             <el-row class="mainmsg">
               <el-col :span="3" class="all">
                 <div @click="allbt" class="iconfont icon text_cen" :class="[all === true ? icon[2] : '']"></div>
               </el-col>
               <el-col :span="3">
                  <div class="icon iconfont icon-shanchu text_cen" @click="delistbt"></div>
                </el-col>
               <el-col :span="15" class="text_inout">1</el-col>
               <el-col :span="3">
                 <el-row>
                   <el-col :span="8">
                     <div class="icon iconfont icon-shanchu text_cen"></div>
                   </el-col>
                   <el-col :span="8">
                     <div class="icon iconfont icon-shanchu text_cen"></div>
                   </el-col>
                   <el-col :span="8">
                     <div class="icon iconfont icon-shanchu text_cen"></div>
                   </el-col>
                 </el-row>
               </el-col>
             </el-row>
             <el-row class="maindata">
               <el-col :span="24" class="title">
                 <el-row>
                   <el-col :span="7" class="text_cen">商品</el-col>
                   <el-col :span="4">订单</el-col>
                   <el-col :span="3">买家</el-col>
                   <el-col :span="3">金额</el-col>
                   <el-col :span="3">状态</el-col>
                   <el-col :span="4" class="text_inout">1</el-col>
                 </el-row>
               </el-col>
               <el-col :span="24">
                 <el-row class="list" v-for="(v, key) in checklist" :key="key">
                   <el-col :span="7">
                     <el-row>
                       <el-col :span="3"><div @click="checkbt(key)" class="check icon iconfont" :class="[icheck.indexOf(key) !== -1 ? icon[2] : '']"></div></el-col>
                       <el-col :span="3"><img src="../assets/img/shapimg.png" alt="" style="width: 50px;height: 50px;"></el-col>
                       <el-col :span="18" class="text_left">
                         <div style="height: 50px; display: table;padding: 0 24px">
                           <span  style="font-size: 12px;display:table-cell; vertical-align:middle;line-height: 18px;">
                             吊带鱼尾裙套装2017夏季新款韩版 时尚荷叶边两件套女小碎花连衣裙
                           </span>
                         </div>
                       </el-col>
                     </el-row>
                   </el-col>
                   <el-col :span="4">
                     <div style="height: 50px; display: table;">
                       <div style="display:table-cell; vertical-align:middle;line-height: 18px;">
                         <div>订单编号：58DA18FE1FD77</div>
                         <div>下单时间：2017-06-12</div>
                       </div>
                     </div>
                   </el-col>
                   <el-col :span="3">
                     <div style="height: 50px; display: table;">
                       <div style="display:table-cell; vertical-align:middle;line-height: 18px;">
                         <div>隔壁老王他邻居</div>
                         <div>ID:6352</div>
                       </div>
                     </div>
                   </el-col>
                   <el-col :span="3" style="line-height: 50px; color: #d65059;">
                     <div>¥ 138.00</div>
                   </el-col>
                   <el-col :span="2" style="line-height: 50px; color: #89dad8;letter-spacing: 2px">
                     <div>已支付</div>
                   </el-col>
                   <el-col :span="5" class="">
                      <el-row style="">
                        <el-col :span="4">  <div class="icon iconfont icon-gengduo text_cen"></div></el-col>
                        <el-col :span="4">
                          <el-popover
                            placement="top-start"
                            width="150"
                            trigger="hover"
                            content="查看佣金">
                            <el-button slot="reference">
                              <div class="icon iconfont icon-yongjin text_cen"></div>
                            </el-button>
                          </el-popover>

                        </el-col>
                        <el-col :span="4">  <div class="icon iconfont icon-chezi text_cen"></div></el-col>
                        <el-col :span="4">  <div class="icon iconfont icon-renwu text_cen"></div></el-col>
                        <el-col :span="8" style="line-height: 50px;">
                          <span class="send">立即发货</span>
                        </el-col>
                      </el-row>
                   </el-col>
                 </el-row>
               </el-col>
             </el-row>
           </el-col>
        </el-row>
      </el-col>
    </el-row>
  </div>
</template>

<script>
/* eslint-disable indent */
  import headernav from './headernav'
  import content from './content'
  export default {
  data () {
    return {
      data: '',
      icheck: [],
      all: false,
      checklist: [1, 2, 3, 4, 5, 6],
      openlist: [], // 子导航判断
      selectlist: [], // 选择判断
      list: [
        {
          value: 300,
          title: '普通商品'
        },
        {
          value: 218,
          title: '已上架'
        },
        {
          value: 26,
          title: '待上架'
        },
        {
          value: 69,
          title: '已售完 '
        },
        {
          value: 126,
          title: '积分商品  '
        }
      ], // 左导航子类
      icon: ['icon-xiaotuziCduan_1', 'icon-xiaotuziCduan_', 'icon-dagou', 'icon-dian-copy'] // 各种切换的图标
    }
  },
  mounted () {
    this.$nextTick(function () {
      this.getData()
    })
  },
  components: {
      'my-Header': headernav,
      'my-Content': content
  },
  computed: {
  },
  watch: {
    icheck (e) { // 实时判断是否全选
      e.length === this.checklist.length && this.checklist.length > 0 ? this.all = true : this.all = false
    }
  },
  methods: {
    getData () {},
    opensonbt (e) { // 是否打开子导航
      if (this.openlist.length === 0) {
        this.openlist.push(e)
      } else {
        this.openlist[0] === e ? this.openlist.splice(0, 1) : this.openlist.splice(0, 1, e)
      }
      this.selectlist = []
    },
    selectsonbt (e) { // 判断点击的子导航
      if (this.selectlist.length === 0) {
        this.selectlist.push(e)
      } else {
        this.selectlist.splice(0, 1, e)
      }
    },
    checkbt (e) { // 勾选
      this.icheck.indexOf(e) !== -1 ? this.icheck.splice(this.icheck.indexOf(e), 1) : this.icheck.push(e)
    },
    allbt () {
      if (!this.all) {
        for (var v in this.checklist) {
          this.icheck.push(parseInt(v))
        }
      } else {
        this.icheck = []
      }
    },
    delistbt () {
      if (this.icheck.length !== 0) { // 根据下标删除, 如果有ID 根据ID删除更加快捷 但是实际开发中只需要把选中的ID传给后台删除
        this.$confirm('确认删除选中？')
          .then(e => {
            for (var i = 0; i < this.icheck.length; i++) {
              this.checklist.splice(this.icheck[i], 1)
              for (var j = 0; j < this.icheck.length; j++) { // 因为删除的原因 原checklist 之前的下标需要减一
                     this.icheck[j] = this.icheck[j] - 1
              }
            }
            this.icheck = []
          })
      } else {
        this.$message.error('错了哦，没有选中')
      }
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style lang="sass">
  @import '../assets/css/main'
  .index
    .userinfo
      padding: 18px
      font-size: 16px
      margin-right: 5px
      border-bottom: 1px solid #e8e8e8
      img
        width: 60px
        height: 60px
        border-radius: 50%
        border: 3px solid #fff
      .name
        font-size: 16px
        line-height: 24px
        padding-top: 10px
      .order
        font-size: 12px
        padding: 5px
        color: #929393
        .tip
          color: #fff
          background: red
          padding: 3px 4px
          border-radius: 5px
    .left_nav
      padding: 30px
      font-size: 15px
      .iconfont
        line-height: 20px
      .left_nav_item
        padding: 10px 0
        padding-bottom: 20px
      .left_nav_son
        font-size: 14px
        padding: 8px 0
      .left_nav_son.active
        color: #3399ff
    .mian_content
      .mainmsg
        padding: 5px 0 5px 10px
        margin-top: 10px
        margin-right: 15px
        font-size: 14px
        background: #fff
        border-radius: 3px
        .all::after
          content: '全选'
          position: absolute
          left: 38px
          top: 6px
        .all div
            width: 18px
            height: 18px
            border-radius: 50%
            border: 1px solid #ebebeb
        .iconfont
          position: relative
          font-size: 13px
          border-radius: 50%
          width: 20px
          height: 20px
          color: #96a2a8
          background: #e9edef
        .icon-dagou
          color: #23b8fd
        .iconfont::before
          position: absolute
          left: 0
          right: 0
          margin-top: 4px
    .maindata
      background: #fff
      font-size: 14px
      color: #202020
      margin-top: 3px
      padding-top: 3px
      margin-right: 15px
      border-radius: 3px
      .title
        background: #e9edef
        color: #929fa5
        line-height: 40px
      .list
        padding: 20px 10px
        font-size: 12px
        .check
          @include brc(20px,20px,#eaeaea)
          margin-top: 14px
          text-align: center
        .check.iconfont
          font-size: 16px
          color: #23b8fd
        .iconfont
          position: relative
          margin-top: 15px
          font-size: 13px
          border-radius: 50%
          width: 20px
          height: 20px
          color: #96a2a8
          background: #e9edef
        .iconfont::before
          position: absolute
          left: 0
          right: 0
          margin-top: 4px
        .send
          @include pbr(4px, 10px, 10px)
          background: #e9edef
        .el-button
          padding: 0px
          border: 0px
        .el-button:hover
          background: 0
          .iconfont:hover
            color: #00afff
</style>
