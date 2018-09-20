<template>
	<div class="wrapper">
		<div class="cm-header">
			<i style="left:5px">&lt;</i>
			<div class="year-month">
				<span class="year">{{date.year}}年{{date.month}}月</span>
				
				<!-- <span class="month">月</span> -->
			</div>
			<i style="right:5px">&gt;</i>
		</div>
		<div class="week">
			<div v-for='item in week' :key="item">{{item}}</div>
		</div>
		<ul class="day">
			<li v-for='(item,i) in dayList' :key="i" :class="{gray: item.day.getMonth()+1 ===date.month }">
				{{item.day.getDate()}}
			</li>
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
			},
			week: ['一','二','三','四','五','六','日'],
			dayList: []
		};
	},
	methods:{
		init(){
			let now = new Date()
			now.setDate(1)
			this.date = {
				year: now.getFullYear(),
				month: add0(now.getMonth()+1),
				day: now.getDate()
			}

			let weekOne = now.getDay() //1号的星期
			let timeOne = now.getTime() //当前月1号的时间戳
			weekOne = weekOne ===0 ? 7: weekOne
			//加载1号前的日期
			for (let i = weekOne-1; i > 0; i--) {
				let dayOne = new Date(timeOne)
				dayOne.setDate(dayOne.getDate() - i)
				let dayLabel = {
					day: dayOne
				}

				let year = dayOne.getFullYear()
				let month = dayOne.getMonth()
				let day = dayOne.getDate()
				this.list.forEach(item => {
					let t  = new Date(item)
					//判断当天是否有标记
					if(
						t.getFullYear() ===  year &&
						t.getMonth() ===  month &&
						t.getDate() === day
					){
						dayLabel.label = item.label
					}
				});
				console.log
				this.dayList.push(dayLabel)
			}

			for (let i = 0; i < array.length; i++) {
				
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
$bgColor: #1a52f1cf;
li{list-style: none;}
.wrapper{
	width: 500px;
	.week{
		display: flex;
		background-color: $bgColor;
		>div{
			flex:1;
			line-height: 2;
			color: #ffffff;
		}
	}
	.day{
		display: flex;
		>li{
			flex: 1
		}
	}
}
.cm-header{
	width: 500px;
	height: 30px;
	background: $bgColor;
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
		letter-spacing: 2px;
	}
}
.cm-header i{
	position: absolute;
	color: $color;
	cursor: pointer;
}
</style>

