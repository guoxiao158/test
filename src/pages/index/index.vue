<template>
  <view class="index">
    <text>msg：{{ msg }}</text>
    	<input
				type="text"
				class="input-search"
				v-model="keyword"
				id="searchInput"
				placeholder="搜索数据"
			/>
      	<input
				type="text"
				class="input-search"
				v-model="msg"
				placeholder="搜索数据"
			/>
		<view @tap="handleClear">关闭</view>
    <view>{{keyword}}</view>
  </view>
</template>

<script>
import { ref,reactive,toRefs } from 'vue'
import './index.scss'

export default {
  setup () {
    const state = reactive({
			keyword: ''
		});
    const msg = ref('Hello world');
    const handleClear = (e) => {
			state.keyword = '';
      msg.value="";
			console.log(state);
	
			setTimeout(() => {
				console.log(document.getElementById('searchInput').value);
				document.getElementById('searchInput').value = '';
				console.log(document.getElementById('searchInput').value);
			}, 1000);
		};
    return {
      ...toRefs(state),
      handleClear,
      msg
    }
  }
}
</script>
