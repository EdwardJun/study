<template>
  <div class="test-page">
    <div class="nav">
      <div class="nav-border">
        <div class="nav-title" :class="{active: currshow == 'message'}" @click="switchNavTitle('message')">消息</div>
        <div class="nav-title" :class="{active: currshow == 'contact'}" @click="switchNavTitle('contact')">联系人</div>
      </div>
    </div>
    <div class="list-wrap" :class="{active: currshow == 'contact'}">
      <scroll-view scroll-y class="mes-wrap" @scroll="doMesScroll" id="mesEle" :style="{height: mesHeight + 'px'}">
        <div class="item-div" v-for="(item, itemIndex) in mesDataList" :key="itemIndex">{{item}}</div>
        <div class="data-load-tip" v-show="dataLoad">加载数据</div>
      </scroll-view>
      <div class="contact-wrap">222</div>
    </div>
  </div>
</template>

<script>
  import Modo from 'modo-ui'
  const Api = Modo.Api

  export default {
    data () {
      return {
        currshow: '',
        dataLoad: false,
        mesHeight: 600,
        mesDataList: ['测试','测试','测试','测试','测试','测试','测试','测试','测试','测试'],
        isAddData: false
      }
    },
    mounted() {
      this.switchNavTitle(),
      this.initMesScrollH()
    },
    
    methods: {
      switchNavTitle(show) {
        let that = this
        show = show || 'message'
        that.currshow = show
      },
      initMesScrollH() {
        let that = this
        let viewHeight = wx.getSystemInfoSync().windowHeight
        console.log(viewHeight)
        that.mesHeight = viewHeight -50
      },
      doMesScroll(event) {
        let that = this
        //console.log(event) //scroll-view组件中有默认转进event参数
        let eventObj = event.mp.detail
        let mesScrollTop = eventObj.scrollTop //滚动条滑动的距离
        let mesScrollHeight = eventObj.scrollHeight //元素可以滚动的高度
        if(mesScrollTop + that.mesHeight * 1.2 >= mesScrollHeight) {
          that.queryMesData()
        }
      },
      queryMesData() {
        let that = this
        that.dataLoad = true
        if(that.isAddData) {
          return 
        }
        that.isAddData = true
        that.mesDataList.push('1','2','3','4','5')
        setTimeout(() => {
          that.dataLoad = false
          that.isAddData = false
        },3000);
      }
    }
  }
</script>

<style lang="scss" scoped>
  .test-page {
    width: 100%;
    overflow-x: hidden;
    .nav {
      width: 100%;
      height: 100px;
      display: flex;
      justify-content: center;
      align-items: center;
      .nav-border {
        display: flex;
        justify-content: center;
        align-items: center;
        width: 300px;
        border: 1px solid #F66;
        border-radius: 10px;
        .nav-title {
          display: flex;
          flex: 1;
          justify-content: center;
          align-items: center;
          width: 144px;
          height: 54px;
          text-align: center;
          color: #F66;
          &.active {
            background-color: #F66;
            color: #ffffff;
          }
        }
      }
    }
    .list-wrap {
      width: 100%;
      display: flex;
      transition: all 0.5s;
      &.active {
        transform: translateX(-100%);
      }
      &>div {
        flex: 0 0 100%;
        width: 100%;
        height: 100%;
      }
      .mes-wrap {
        flex: 0 0 100%;
        width: 100%;
        height: 100%;
        .item-div {
          width: 100%;
          height: 160px;
          display: flex;
          justify-content: center;
          align-items: center;
        }
      }
      .data-load-tip {
        text-align: center;
      }
    }
  }
</style>
