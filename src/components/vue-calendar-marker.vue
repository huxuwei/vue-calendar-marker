<template>
	<div class="wrapper">
		<div class="cm-header">
			<span style="left:5px">&lt;</span>
			<span style="right:5px">&gt;</span>
		</div>
		<ul >
			<li></li>
		</ul>
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
		},
		initDate:{
			type: Object | String,
			default(){
				return new Date()
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

.wrapper{
	width: 100%;
}
.cm-header{
	width: 500px;
	height: 30px;
	background: #1a52f1cf;
	position: relative;
	display: flex;
	align-items: center;

}
.cm-header span{
	position: absolute;
	color: #ffffff;
}
</style>

