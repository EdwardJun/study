<template>
  <div class="project-page">
    <div class="nav">
      <scroll-view class="nav-scroll" scroll-x style="width: auto;overflow:hidden;">
        <div v-for="(nav,index) in navList" :key="index" class="nav-item">
          <a :class="{active: index==navIndex}" @click="changeActive(index)" v-text="nav"></a>
        </div>
      </scroll-view>
    </div>
    <scroll-view scroll-y class="project-con" :style="{height: scrollHeight + 'rpx'}" :scroll-into-view="proIndex" scroll-with-animation="true" enable-back-to-top="false">
      <div class="recommen-item" id="am">
        <div class="recommen-item-title">
          <span class="title-desc">各式按摩</span>
          <span class="all">全部<img src="/static/img/arrow_right_red.png" alt=""></span>
        </div>
        <div class="recommen-con">
          <div class="recommen-border">
            <img class="recommen-img" src="/static/img/test2.jpg" alt="">
            <div class="recommen-shade">面部spa</div>
            <div class="recommen-footer">
              <span class="recommen-footer-left"><span class="yuan">￥</span>698</span>
              <span class="recommen-footer-right">120分钟</span>
            </div>
          </div>
          <div class="recommen-border">
            <img class="recommen-img" src="/static/img/test2.jpg" alt="">
            <div class="recommen-shade">面部spa</div>
            <div class="recommen-footer">
              <span class="recommen-footer-left"><span class="yuan">￥</span>698</span>
              <span class="recommen-footer-right">120分钟</span>
            </div>
          </div>
        </div>
      </div>
      <div class="recommen-item" id="zy">
        <div class="recommen-item-title">
          <span class="title-desc">大堂足浴</span>
          <span class="all">全部<img src="/static/img/arrow_right_red.png" alt=""></span>
        </div>
        <div class="recommen-con">
          <div class="recommen-border">
            <img class="recommen-img" src="/static/img/test2.jpg" alt="">
            <div class="recommen-shade">面部spa</div>
            <div class="recommen-footer">
              <span class="recommen-footer-left"><span class="yuan">￥</span>698</span>
              <span class="recommen-footer-right">120分钟</span>
            </div>
          </div>
          <div class="recommen-border">
            <img class="recommen-img" src="/static/img/test2.jpg" alt="">
            <div class="recommen-shade">面部spa</div>
            <div class="recommen-footer">
              <span class="recommen-footer-left"><span class="yuan">￥</span>698</span>
              <span class="recommen-footer-right">120分钟</span>
            </div>
          </div>
        </div>
      </div>
      <div class="recommen-item" id="spa">
        <div class="recommen-item-title">
          <span class="title-desc">SPA</span>
          <span class="all">全部<img src="/static/img/arrow_right_red.png" alt=""></span>
        </div>
        <div class="recommen-con">
          <div class="recommen-border">
            <img class="recommen-img" src="/static/img/test2.jpg" alt="">
            <div class="recommen-shade">面部spa</div>
            <div class="recommen-footer">
              <span class="recommen-footer-left"><span class="yuan">￥</span>698</span>
              <span class="recommen-footer-right">120分钟</span>
            </div>
          </div>
          <div class="recommen-border">
            <img class="recommen-img" src="/static/img/test2.jpg" alt="">
            <div class="recommen-shade">面部spa</div>
            <div class="recommen-footer">
              <span class="recommen-footer-left"><span class="yuan">￥</span>698</span>
              <span class="recommen-footer-right">120分钟</span>
            </div>
          </div>
        </div>
      </div>
      <div class="recommen-item" id="js">
        <div class="recommen-item-title">
          <span class="title-desc">酒水</span>
          <span class="all">全部<img src="/static/img/arrow_right_red.png" alt=""></span>
        </div>
        <div class="recommen-con">
          <div class="recommen-border">
            <img class="recommen-img" src="/static/img/test2.jpg" alt="">
            <div class="recommen-shade">面部spa</div>
            <div class="recommen-footer">
              <span class="recommen-footer-left"><span class="yuan">￥</span>698</span>
              <span class="recommen-footer-right">120分钟</span>
            </div>
          </div>
          <div class="recommen-border">
            <img class="recommen-img" src="/static/img/test2.jpg" alt="">
            <div class="recommen-shade">面部spa</div>
            <div class="recommen-footer">
              <span class="recommen-footer-left"><span class="yuan">￥</span>698</span>
              <span class="recommen-footer-right">120分钟</span>
            </div>
          </div>
        </div>
      </div>
      <div class="recommen-item" id="ls">
        <div class="recommen-item-title">
          <span class="title-desc">零食</span>
          <span class="all">全部<img src="/static/img/arrow_right_red.png" alt=""></span>
        </div>
        <div class="recommen-con">
          <div class="recommen-border">
            <img class="recommen-img" src="/static/img/test2.jpg" alt="">
            <div class="recommen-shade">面部spa</div>
            <div class="recommen-footer">
              <span class="recommen-footer-left"><span class="yuan">￥</span>698</span>
              <span class="recommen-footer-right">120分钟</span>
            </div>
          </div>
          <div class="recommen-border">
            <img class="recommen-img" src="/static/img/test2.jpg" alt="">
            <div class="recommen-shade">面部spa</div>
            <div class="recommen-footer">
              <span class="recommen-footer-left"><span class="yuan">￥</span>698</span>
              <span class="recommen-footer-right">120分钟</span>
            </div>
          </div>
        </div>
      </div>
      <div class="recommen-item" id="vip1">
        <div class="recommen-item-title">
          <span class="title-desc">VIP1</span>
          <span class="all">全部<img src="/static/img/arrow_right_red.png" alt=""></span>
        </div>
        <div class="recommen-con">
          <div class="recommen-border">
            <img class="recommen-img" src="/static/img/test2.jpg" alt="">
            <div class="recommen-shade">面部spa</div>
            <div class="recommen-footer">
              <span class="recommen-footer-left"><span class="yuan">￥</span>698</span>
              <span class="recommen-footer-right">120分钟</span>
            </div>
          </div>
          <div class="recommen-border">
            <img class="recommen-img" src="/static/img/test2.jpg" alt="">
            <div class="recommen-shade">面部spa</div>
            <div class="recommen-footer">
              <span class="recommen-footer-left"><span class="yuan">￥</span>698</span>
              <span class="recommen-footer-right">120分钟</span>
            </div>
          </div>
        </div>
      </div>
      <div class="recommen-item" id="vip2">
        <div class="recommen-item-title">
          <span class="title-desc">VIP2</span>
          <span class="all">全部<img src="/static/img/arrow_right_red.png" alt=""></span>
        </div>
        <div class="recommen-con">
          <div class="recommen-border">
            <img class="recommen-img" src="/static/img/test2.jpg" alt="">
            <div class="recommen-shade">面部spa</div>
            <div class="recommen-footer">
              <span class="recommen-footer-left"><span class="yuan">￥</span>698</span>
              <span class="recommen-footer-right">120分钟</span>
            </div>
          </div>
          <div class="recommen-border">
            <img class="recommen-img" src="/static/img/test2.jpg" alt="">
            <div class="recommen-shade">面部spa</div>
            <div class="recommen-footer">
              <span class="recommen-footer-left"><span class="yuan">￥</span>698</span>
              <span class="recommen-footer-right">120分钟</span>
            </div>
          </div>
        </div>
      </div>
    </scroll-view>
  </div>
</template>

<script>
  import Modo from 'modo-ui'
  const Api = Modo.Api
  export default {
    data () {
      return {
        navList: ['各式按摩','大堂足浴','SPA','酒水','零食','VIP1','VIP2'],
        navIndex: 0, //nav active状态的下标
        scrollHeight: 1000,
        projectScrollTop: 500,
        proIndex: ''
      }
    },
    onShow() {
      this.initListHeight()
    },
    methods: {
      changeActive(index) {
        let dom = ''
        this.navIndex = index
        switch(index) {
          case 0: dom = 'am';
            break;
          case 1: dom = 'zy';
            break;
          case 2: dom = 'spa';
            break;
          case 3: dom = 'js';
            break;
          case 4: dom = 'ls';
            break;
          case 5: dom = 'vip1';
            break;
          default: dom = 'vip2';
        }
        this.proIndex = dom
      },
      // 动态设置list的高度
      initListHeight() {
        let that = this
        let viewHeight = wx.getSystemInfoSync().windowHeight
        that.scrollHeight = viewHeight*2 - 44 - 64
      },
    }
  }
</script>

<style lang="scss">
  @import "~asset/css/_global";
  
  .project-page {
    .nav {
      width: auto;
      height: 80px;
      .nav-scroll {
        height: 100%;
        overflow: hidden;
        white-space: nowrap;
        .nav-item {
          display: inline-block;
          width: 150px;
          height: 80px;
          line-height: 80px;
          box-sizing: border-box;
          text-align: center;
          a {
            position: relative;
            font-size: 30px;
            &.active {
              &.active::after {
                position: absolute;
                left: 20px;
                bottom: 0;
                content: " ";
                display: inline-block;
                width: 70%;
                border: 1px solid red;
                margin-top: 5px;
                text-align: center;
              }
            }
          }
        }
      }
    }
    .project-con {
      .recommen-item {
        margin-top: 50px;
        .recommen-item-title {
          width: 100%;
          height: 35px;
          display: flex;
          .title-desc {
            display: inline-block;
            flex: 1;
            color: #333333;
            font-size: 33px;
          }
          .title-desc:before {
            content: " ";
            display: inline-block;
            width: 0;
            height: 38px;
            border: 0;
            border-left: 5px solid #f66;
            margin: 0 20px;
            vertical-align: text-bottom;
          }
          .all {
            width: 150px;
            flex: 0 0 150;
            color: #ff8c85;
            img {
              width: 13px;
              height: 21px;
              margin: 0 39px 0 16px;
            }
          }
        }
        .recommen-con {
          padding: 36px 0 0 38px;
          display: flex;
          .recommen-border {
            flex: 1;
            flex: 0 0 323px;
            position: relative;
            width: 323px;
            height: 406px;
            box-shadow: 4px  6px 10px rgb(182, 180, 180);
            margin-right: 30px;
              .recommen-img {
                width: 323px;
                height: 321px;
              }
              .recommen-shade {
                box-sizing: border-box;
                position: absolute;
                bottom: 85px;
                padding-left: 15px;
                width: 100%;
                height: 57px;
                line-height: 57px;
                font-size: 31px;
                color: #FFFFFF;
                background-color: #616161;
                opacity: 0.7;
                filter:alpha(opacity=70);
              }
            .recommen-footer {
              position: absolute;
              top: 321px;
              width: 100%;
              height: 85px;
              line-height: 85px;
              display: flex;
              align-items: baseline;
              .recommen-footer-left {
                flex: 1;
                margin-left: 14px;
                font-size: 37px;
                color: #ff8c85;
                .yuan {
                  font-size: 23px;
                }
              }
              .recommen-footer-right {
                flex: 1;
                text-align: right;
                margin-right: 10px;
                font-size: 23px;
                color: #616161;
              }
            }
          }
        }
      }
    }
  }
</style>
