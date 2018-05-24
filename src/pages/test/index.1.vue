<template>
  <div class="test-page">
    <div class="checkedItem">
      <div>
        <label for="allCheck" @click="checkAll"><input type="checkbox" v-model="isAllCheck">全选</label>{{isAllCheck}}
      </div>
      <checkbox-group>
        <label class="checkbox" v-for="(item,itemIndex) in items" :key="itemIndex">
          <checkbox :value="item.name" v-model="item.checked" />{{item.value}}
        </label>
      </checkbox-group>{{checkList}}
    </div>
  </div>
</template>

<script>
  import Modo from 'modo-ui'
  const Api = Modo.Api

  export default {
    data () {
      return {
        isAllCheck: true,
        items: [
          {name: 'USA', value: '美国'},
          {name: 'CHN', value: '中国'},
          {name: 'BRA', value: '巴西'},
          {name: 'JPN', value: '日本'},
          {name: 'ENG', value: '英国'},
          {name: 'TUR', value: '法国'},
        ],
        checkList: []
      }
    },
    mounted() {
      /* let that = this
      that.items.forEach((obj,index) => {
        obj.checked = false
      }); */
      /* numlist() {
        return this.Nums.map(item => { return { ... item } })
      } */
    },
    methods: {
      checkAll() {
        let that = this
        console.log(that.checkList)
        console.log(that.isAllCheck)
        this.$nextTick(() => {
          console.log(that.isAllCheck)
        });
        if(that.isAllCheck) {
          that.checkList = []
        }else {
          that.checkAll = []
          that.items.array.forEach((item,index) => {
            that.checkList.push(item.name)
          });
        }
      },
    },
    watch: {
      'checkList': {
        handler: function(val, oldVal) {
          if(val.length === this.items.length){
            this.isAllCheck = true
          }else {
            this.isAllCheck = false
          }
        },
        deep: true
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
