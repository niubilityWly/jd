<template>
<div id="store">
<div class="proListBox" v-if="proData.length">
	<ul class="storeTitle clearfix">
		<li>
			<input type="checkbox" name="selectAll" @click="selectAll()" id="setAll">
			<label for="selectAll">全选</label>
		</li>
		<li>商品</li>
		<li>单价</li>
		<li>数量</li>
		<li>小计</li>
		<li>操作</li>
	</ul>
	<ul class="prolist">
		<li v-for="(item,index) in proData">
		<div class="listLeft">
			<div class="checkBox">
			<input type="checkbox" class="checkbox" v-model="checkIndex" name="selectIndex" :value="index"/>
			</div>
			<img :src="item.imgUrl">
			<span class="proTitle">{{item.proTitle}}</span>
			<span class="proSize">{{item.proSize}}</span>
		</div>
			<span class="proPrice">￥{{item.proPrice}}</span>
			<div class="changeNum">
				<button @click="minus(index)">-</button>
				<input type="text" name="" :value="item.num" v-model="item.num" />
				<button @click="add(index)">+</button>
			</div>
			<span class="totalPrice">￥{{item.proPrice * item.num}}</span>
			<a href="#" @click="deleteThis(index)">删除</a>
		</li>
	</ul>
	<ul>
		<li>
		</li>
		<li></li>
		<li></li>
		<li></li>
		<li></li>
	</ul>
</div>
<div class="noPro clearfix" v-else>
	<img class="left" src="../assets/no-login-icon.png" height="55" width="71">
	<div class="left">
		<p>购物车空空的哦~，去看看心仪的商品吧~</p>
		<a href="#">去购物></a>
	</div>
</div>
	
</div>
</template>

<script>
var onoff = true;
export default {
  name: 'store',
  data(){
  	return{
  		proData:proData,
  		checkIndex:[],
  		total:0,
  		allCount:0
  	}
  },
  methods:{
  		add:function(index){
  			this.proData[index].num ++
  		},
  		minus:function(index){
  			if(this.proData[index].num >1 ){
  				this.proData[index].num --
  			}
  		},
  		deleteThis:function(index){
  			this.proData.splice(index,1)
  		},
  		selectAll:function(){
  			var setAllStatus = document.getElementById("setAll").checked;
  			var checkArr = this.checkIndex;
  			if(setAllStatus == true){
  				this.proData.forEach(function(item,index,array){
  					checkArr.push(index);
  					console.log(checkArr);
  				})
  			}else{
  				checkArr = [];
  			}
  			this.checkIndex = checkArr;	

  		}
  }
}

var proData = [
  	{
  		"id":"A101",
  		"imgUrl":require("../assets/pro1.jpg"),
  		"proTitle":"西门子XXXX洗衣机",
  		"proSize":"爆款银色8公斤",
  		"proPrice":"3498.00",
  		"num":"2"
  	},
  	{
  		"id":"A102",
  		"imgUrl":require("../assets/pro2.jpg"),
  		"proTitle":"飞利浦XXXX电视机",
  		"proSize":"43英寸4K-十七核",
  		"proPrice":"2499.00",
  		"num":"1"
  	},
  	{
  		"id":"A103",
  		"imgUrl":require("../assets/pro3.jpg"),
  		"proTitle":"康佳XXXX电视机",
  		"proSize":"43英寸4K 10核",
  		"proPrice":"2288.00",
  		"num":"1"
  	}
  ]
</script>