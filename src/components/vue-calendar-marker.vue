<template>
	<div class="wrapper">
		<div class="cm-header">
			<i style="left:5px">&lt;</i>
			<div class="year-month">
				<span class="year">{{date.year}}</span>
				<span class="month">{{date.month}}</span>
			</div>
			<i style="right:5px">&gt;</i>
		</div>
		<ul >
			<li></li>
		</ul>
	</div>
</template>

<script>
import {add0} from './until.js'
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
    return {
			date:{
				year: '',
				month: '',
				day: ''
			}
		};
	},
	methods:{
		init(){
			let now = new Date()
			this.date = {
				year: now.getFullYear(),
				month: add0(now.getMonth()+1),
				day: now.getDate()
			}
		}
	},
	created(){
		this.init()
	}
};
</script>

<style lang='scss' scoped>
$color:#ffffff;

li{list-style: none;}
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
	justify-content: space-around;
}
.year-month{
	flex: 1;
	height: inherit;
	display: flex;
	justify-content: center;
	align-items: center;
	overflow: hidden;
	span{
		color: $color;
		margin-left: 1em;
	}
}
.cm-header i{
	position: absolute;
	color: $color;
	cursor: pointer;
}
</style>

