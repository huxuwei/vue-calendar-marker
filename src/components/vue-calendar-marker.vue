<template>
	<div>
		<div>
			<span><</span>
			<span>></span>
		</div>
	</div>
</template>

<script>
export default {
	name: "vue-calender-marker",
	props:{
		list: {
			type: Array,
			default(){
				return []
			}
		}
	},
  data() {
    return {};
	},
	methods:{
		init(){

		}
	}
};
</script>

<style  scoped>

</style>

