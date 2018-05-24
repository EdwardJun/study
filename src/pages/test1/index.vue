<template>
  <div class="test-page">
    <div class="nav">
      <div class="nav-border">
        <div class="nav-title" :class="{active: currshow == 'message'}" @click="switchNavTitle('message')">消息</div>
        <div class="nav-title" :class="{active: currshow == 'contact'}" @click="switchNavTitle('contact')">联系人</div>
      </div>
    </div>
    <div class="list-wrap" :class="{active: currshow == 'contact'}">
      <div class="mes-wrap">111</div>
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
        currshow: ''
      }
    },
    mounted() {
      this.switchNavTitle()
    },
    methods: {
      switchNavTitle(show) {
        let that = this
        show = show || 'message'
        that.currshow = show
      }
    }
  }
</script>

<style lang="scss" scoped>
  .test-page {
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
    }
  }
</style>
