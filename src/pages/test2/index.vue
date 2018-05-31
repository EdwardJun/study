<template>
  <div class="order-page">
    <div class="nav-border">
      <div class="nav" :class="{showBorderBottom: isShowNavBorder}">
        <div class="nav-div">
          <a v-for="(item, itemIndex) in navList" :key="itemIndex" :class="{active: itemIndex==navIndex && itemIndex != 3,triangleActive: isTriangle}" v-text="itemIndex==3? orderBtnName: item" @click="changeActive(itemIndex)"></a>
        </div>
      </div>
    </div>
    <div class="order-dialog" :class="{show: isShowDialog}" @click="cancleShowDialog()">
      <div class="order-dialog-con" :class="{show: isShowDialogCon}" @click.stop="doShowDialogCon()">
        <div class="order-line">
          <div class="order-btn" :class="{active: orderBtn.id == orderBtnId}" @click.stop="chooseOrder($event)" :data-name="orderBtn.name" 
          :data-id="orderBtn.id" v-text="orderBtn.name" v-for="(orderBtn,orderBtnIndex) in orderBtnList" :key="orderBtnIndex"></div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
  import Modo from 'modo-ui'
  const Api = Modo.Api

  export default {
    data () {
      return {
        navList: ['未使用','已使用','已过期','全部类型'],
        navIndex: 0, //nav active下标
        isShowNavBorder: false,
        isTriangle : false,
        isShowDialog: false,
        isShowDialogCon: false,
        orderBtnId: 'allType',
        orderBtnName: '全部类型',
        orderBtnList: [
          {id: 'allType', name: '全部类型'},
          {id: 'ckxm', name: '次卡项目'},
          {id: 'hhtc', name: '混合套餐'},
          {id: 'jflp', name: '积分礼品'},
          {id: 'xsg', name: '限时购'},
          {id: 'dzj', name: '点钟劵'},
          {id: 'dzp', name: '大转盘'},
          {id: 'mdyl', name: '买单有礼'},
          {id: 'pt', name: '拼团'}

        ]
      }
    },
    computed: {
    },
    methods: {
      changeActive(itemIndex) {
        let that = this
        if(itemIndex == 3) {
          that.doShowDialogCon()
        }else {
          that.navIndex = itemIndex
          that.cancleShowDialog()
        }
      },
      doShowDialogCon() {
        let that = this
        that.isShowNavBorder = true
        that.isShowDialog = true
        setTimeout(() => {
          that.isShowDialogCon = true
        },200)
        setTimeout(() => {
          that.isTriangle = true
        },300)
        
      },
      cancleShowDialog() {
        let that = this
        that.isShowNavBorder = false
        that.isTriangle = false
        that.isShowDialogCon = false
        setTimeout(() => {
          that.isShowDialog = false
        },200)
      },
      chooseOrder(e) {
        let that = this
        let id = e.mp.currentTarget.dataset.id;
        let name = e.mp.currentTarget.dataset.name;
        if(that.orderBtnId != id) {
          that.orderBtnId = e.mp.currentTarget.dataset.id;
          that.orderBtnName = e.mp.currentTarget.dataset.name;
        }
        that.cancleShowDialog()
      }
    }
  }
</script>

<style lang="scss" scoped>
  .order-page {
    background-color: #ffffff;
    .nav-border {
      /* width: 100%;
      height: 99px; */ //暂定
      background-color: #ffffff;
      .nav {
        width: 100%;
        height: 101px;
        &.showBorderBottom{
          border-bottom: 1px solid #d2d2d2;
        }
        .nav-div {
          width: 100%;
          height: 87px;
          display: flex;
          justify-content: center;
          align-items: center;
          a {
            position: relative;
            display: flex;
            flex: 1;
            justify-content: center;
            align-items: center;
            height: 100%;
            text-align: center;
            font-size: 24px;
            font-weight: bold;
            color: #000000;
            &:nth-of-type(3) {
              position: relative;
              &::before {
                position: absolute;
                right: 0;
                content: " ";
                width: 0;
                height: 30%;
                border: 1px solid #d2d2d2;
              }
            }
            &:last-child {
              position: relative;
              flex: 0 0 240px;
              width: 240px;
              &.triangleActive {
                &::before {
                  position: absolute;
                  bottom: -15px;
                  left: 50%;
                  margin-left: -11px;
                  content: " ";
                  width: 0;height: 0;
                  border-width: 22px;
                  border-style: dashed dashed solid dashed;
                  border-color: transparent transparent #d2d2d2 transparent;
                }
                &::after {
                  position: absolute;
                  bottom: -17px;
                  left: 50%;
                  margin-left: -11px;
                  content: " ";
                  width: 0;height: 0;
                  border-width: 22px;
                  border-style: dashed dashed solid dashed;
                  border-color: transparent transparent #ffffff transparent;
                }
              }
            }
            &.active {
              color: #ff8c86;
            }
            &.active::after {
              position: absolute;
              left: 50%;
              bottom: 5px;
              margin-left: -15px;
              content: " ";
              width: 30px;
              border: 3px solid #ff8c86;
            }
          }
        }
      }
    }
    .order-dialog {
      position: absolute;
      top: 103px;
      left: 0;
      width: 100%;
      height: 100%;
      background:rgba(0, 0, 0, 0.35);
      z-index: 5;
      opacity: 0;
      display: none;
      &.show {
        opacity: 1;
        display: inline-block;
        transition: all .5s;
      }
      .order-dialog-con {
        position: absolute;
        top: 0;
        left: 0;
        width: 100%;
        height: auto;
        padding: 13px 0 72px 46px;
        z-index: 6;
        opacity: 0;
        background: #ffffff;
        &.show {
          opacity: 1;
          transition: all .5s;
        }
        .order-line {
          width: 100%;
          display: flex;
          flex-wrap: wrap;
          justify-content: flex-start;
          align-items: center;
          .order-btn {
            display: flex;
            flex: 0 0 134px;
            justify-content: center;
            align-items: center;
            margin-top: 41px;
            margin-right: 41px;
            width: 134px;
            height: 62px;
            border: 1px solid #d2d2d2;
            border-radius: 10px;
            color: #000000;
            font-size: 28px;
            z-index: 7;
            &:last-child {
              margin-right: 0;
            }
            &.active {
              background-color: #ff8c86;
              color: #ffffff;
            }
            &.wrap {
              flex-wrap: wrap;
            }
          }
        }
      }
    }
  }
</style>
