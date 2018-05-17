<template>
  <div class="project-page">
    <div class="nav">
      <scroll-view class="nav-scroll" scroll-x style="width: auto;overflow:hidden;">
        <div v-for="(nav,index) in navList" :key="index" class="nav-item">
          <a :class="{active: index==navIndex}" @click="changeActive(index)" v-text="nav"></a>
        </div>
      </scroll-view>
    </div>
  </div>
</template>

<script>
  import menuItem from '@/components/menuItem'
  import Modo from 'modo-ui'
  const Api = Modo.Api
  export default {
    data () {
      return {
        navList: ['各式按摩','大堂足浴','SPA','酒水','零食','VIP1','VIP2'],
        navIndex: 0
      }
    },
    methods: {
      changeActive(index) {
        this.navIndex = index;
      }
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
  }
</style>
