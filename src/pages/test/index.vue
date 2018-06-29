<template>
  <div class="test-page">
    <div class="checkedItem">
      <div>
        <label for="allCheck" @click="checkAll"><input type="checkbox" id="allCheck" :checked="isAllCheck">全选1</label>
      </div>
      <checkbox-group @change="checkboxChange">
        <label class="checkbox" v-for="(item,itemIndex) in items" :key="itemIndex" @click="checkOne(item,itemIndex)">
          <checkbox :value="item.name" :checked="item.checked" v-model="item.checked"/>{{item.value}}{{item.checked}}
        </label>
      </checkbox-group>
    </div>
  </div>
</template>

<script>
  import Modo from 'modo-ui'
  const Api = Modo.Api

  export default {
    data () {
      return {
        isAllCheck: false,
        childCheck: false,
        items: [
          {name: 'USA', value: '美国',checked: false},
          {name: 'CHN', value: '中国',checked: false},
          {name: 'BRA', value: '巴西',checked: false},
          {name: 'JPN', value: '日本',checked: false},
          {name: 'ENG', value: '英国',checked: false},
          {name: 'TUR', value: '法国',checked: false},
        ],
        numList: []
      }
    },
    methods: {
      checkAll() {
        let that = this
        that.isAllCheck = !that.isAllCheck
        that.items.map((obj,index) => {
          that.$set(obj,'checked',that.isAllCheck)
        })
        // this.items = that.items
      },
      checkOne(obj,index) {
        let that = this
        let checkList = []
        that.items.map((itemObj,itemIndex) => {
          if(itemIndex == index) {
            that.$set(itemObj,'checked',!itemObj.checked)
          }
          if(itemObj.checked) {
            checkList.push(itemObj)
          }
          // this.items = that.items
        })
        if(checkList.length == that.items.length) {
          that.isAllCheck = true
        }else{
          that.isAllCheck = false
        }
      }
    }
  }
</script>

<style lang="scss" scoped>
  .test-page {
    .checkedItem {
      .checkGroup {
        display: flex;
        margin-top: 10px;
        label {
          margin-right: 50px;
          flex: 3;
        }
      }
    }
  }
</style>
