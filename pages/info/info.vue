<template>
	<view>
		state中的token值{{vuex_token}}
		
	</view>
</template>

<script>
	import { mapState } from 'vuex'
	export default {
		data() {
			return {
				
			};
		},
		computed:{
			...mapState(['vuex_token'])
		}
	}
</script>

<style lang="scss">

</style>
