<template>
   <view v-if="masking" class="masking"></view>
  <view class="index">
    <view class="btn-text" 
      :class="{ 'active': pageConfig.type === index }" 
      v-for="(item, index) in btnList"
      @tap="switchType(index)" 
      :key="index">{{ item }}
    </view>
  </view>
</template>

<script>
import { ref, reactive } from 'vue'
import './index.scss'

export default {
  setup () {
    const btnList = ref([ 1,2,3 ])
    const pageConfig = reactive({
      type:0
    })
    const masking = ref(false)

    function switchType(index){
      pageConfig.type = index
      if( index === 1 ){
        masking.value = false
      }else if( index === 2 ){
        masking.value = true
      }
    }
    return {
      btnList,
      pageConfig,
      masking, 

      switchType
    }
  }
}
</script>

<style lang="scss">
.index{
  display: flex;padding-top:100rpx;
  .btn-text{
    width: 150rpx;height: 80rpx;background: blue;color: #fff;margin: 10px 10px;text-align: center;
  }
  .active{border: 1px solid red;}
  
}
  .masking{
    width: 100%;height: 50px; position: fixed; top: 0;left: 0;background: #000;
  }
</style>
