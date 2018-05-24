<template>
  <div class="test-page">
    <div class="checkedItem">
      <div>
        <label for="allCheck" @click="checkAll"><input type="checkbox" id="allCheck" :checked="isAllCheck">全选</label>
      </div>
      <checkbox-group @change="checkboxChange">
        <label class="checkbox" v-for="(item,itemIndex) in items" :key="itemIndex" @click="checkOne(item)">
          <checkbox :value="item.name" :checked="item.checked" v-model="item.checked"/>{{item.value}}
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
          {name: 'USA', value: '美国'},
          {name: 'CHN', value: '中国'},
          {name: 'BRA', value: '巴西'},
          {name: 'JPN', value: '日本'},
          {name: 'ENG', value: '英国'},
          {name: 'TUR', value: '法国'},
        ],
        numList: []
      }
    },
    methods: {
      checkAll() {
        let that = this
        that.isAllCheck = !that.isAllCheck
        that.items.forEach((obj,index) => {
          obj.checked = that.isAllCheck
        });
        this.$nextTick(() => {
          console.log('更新DOM')
        })
      },
      checkboxChange(e) {
        console.log(e.mp.detail.value)
        let that = this
        if(e.mp.detail.value.length == that.items.length){
          that.isAllCheck = true
        }else {
          that.isAllCheck = false
        }
        this.$nextTick(() => {
          console.log('更新DOM')
        })
      },
      checkOne(obj) {
        var that = this
        console.log(obj.name)
        this.items.forEach((item,index) => {
        if(item.name == obj.name) {
          console.log(this.items[this.items.indexOf(item)])
          //this.$set(this.items,this.items[this.items.indexOf(item)].checked,!obj.checked)
          this.$set(this.items,this.items[this.items.indexOf(obj)].checked,!obj.checked)
          console.log(obj.checked)
          this.$nextTick(() => {

          })
          
          }
        });
        
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
