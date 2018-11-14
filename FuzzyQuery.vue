<template>
	<div>
		<input type="text" v-model='search' />
<ul v-for="item in searchData ">
<li>{{item.name}},价格:￥{{item.price}}</li>
</ul>
	</div>
</template>
<script type="text/javascript">
	 export default{
    name: 'chazhao',
    data(){
      return {
      	search: '',
		products: [{
		name: '苹果',
		price: 25,
		category: "水果"
		}, {
		name: '香蕉',
		price: 15,
		category: "水果"
		}, {
		name: '雪梨',
		price: 65,
		category: "水果"
		}, {
		name: '宝马',
		price: 2500,
		category: "汽车"
		}, {
		name: '奔驰',
		price: 10025,
		category: "汽车"
		}, {
		name: '柑橘',
		price: 15,
		category: "水果"
		}, {
		name: '奥迪',
		price: 25,
		category: "汽车"
		}, {
		name: '火龙果',
		price: 25,
		category: "水果"
		}]

      }
  },
   methods: {
    
  },
  computed: {
	searchData: function() {
	var search = this.search;
	var searchVal = '';//搜索后的数据
	if (search) {
	searchVal = this.products.filter(function(product) {
	return Object.keys(product).some(function(key) {
	//搜索所有的内容
	return String(product[key]).toLowerCase().indexOf(search) > -1;
	//只搜索问题内容（某一个key）
	return String(product['questions']).toLowerCase().indexOf(search)>-1;
	})
	})
	return searchVal;
	}
	}
	}

}
</script>