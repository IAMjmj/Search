<template>
  	<div class="search">
		<div class="header">
			<div class="system">数字离校系统</div>
		</div>
		<div class="search_bar">
			<el-input v-model="input" placeholder="请输入搜索内容" class="search_content"></el-input>
			<el-button type="primary" icon="el-icon-search" class="search_btn">全文搜索</el-button>
		</div>
		<div class="main_content clearfix">
			<div class="search_result">
				<div class="result" v-for="(result,index) in viewTable" :key="index">
					<span class="title">{{result.title}}</span>
					<div class="section_content">{{result.content}}</div>
				</div>
				<div class="block page">
					<el-pagination
					@size-change="handleSizeChange"
					@current-change="handleCurrentChange"
					:current-page="currentPage"
					:page-sizes="[100, 200, 300, 400]"
					:page-size="100"
					layout="total, sizes, prev, pager, next, jumper"
					:total="400">
					</el-pagination>
				</div>
			</div>
			<div class="right">
				<el-card class="box-card">
					<div slot="header" class="clearfix">
						<span>{{MsgType}}</span>
						<span class="date">{{date}}</span>
						<!-- <el-button style="float: right; padding: 3px 0" type="text">操作按钮</el-button> -->
					</div>
					<div>
						内容：<div v-html="content" class="content"></div>
					</div>
				</el-card>
			</div>
		</div>
  	</div>

</template>

<script>
  export default {
    name: 'HelloWorld',
    data() {
      	return {
			input:"",
			viewTable: [{
				title:"dfadsfads",
				content:"dsafjkldjfladsjlfjalsdfjladsjfljadslfjladsjfljadslfjlasdjfljasldfjlasdjfljadlsfjladjflajdslfjladsjfladjslfjaldsjfladjslfjaldjflajdlfjadlsjflasdjlfjsaldfjlsdjflajdslfjladljdfdslfjalsdjfladlasldjfladlfadlfldjflajdlkfdjfadsjlfajkdslfladsjkfldajlfladjfljadslfjladljfdlsjfladjklfaslkdjflasdjlkfjal"
			},{
				title:"dfadsfads",
				content:"dsafjkldjfladsjlfjalsdfjladsjfljadslfjladsjfljadslfjlasdjfljasldfjlasdjfljadlsfjladjflajdslfjladsjfladjslfjaldsjfladjslfjaldjflajdlfjadlsjflasdjlfjsaldfjlsdjflajdslfjladljdfdslfjalsdjfladlasldjfladlfadlfldjflajdlkfdjfadsjlfajkdslfladsjkfldajlfladjfljadslfjladljfdlsjfladjklfaslkdjflasdjlkfjal",
				content:"fadsfdfasdfasdfadsf"
			},{
				title:"dfadsfads",
				content:"dfadsfads",
				content:"dsafjkldjfladsjlfjalsdfjladsjfljadslfjladsjfljadslfjlasdjfljasldfjlasdjfljadlsfjladjflajdslfjladsjfladjslfjaldsjfladjslfjaldjflajdlfjadlsjflasdjlfjsaldfjlsdjflajdslfjladljdfdslfjalsdjfladlasldjfladlfadlfldjflajdlkfdjfadsjlfajkdslfladsjkfldajlfladjfljadslfjladljfdlsjfladjklfaslkdjflasdjlkfjal"
			},{
				title:"dfadsfads",
				content:"dfadsfads",
				content:"dsafjkldjfladsjlfjalsdfjladsjfljadslfjladsjfljadslfjlasdjfljasldfjlasdjfljadlsfjladjflajdslfjladsjfladjslfjaldsjfladjslfjaldjflajdlfjadlsjflasdjlfjsaldfjlsdjflajdslfjladljdfdslfjalsdjfladlasldjfladlfadlfldjflajdlkfdjfadsjlfajkdslfladsjkfldajlfladjfljadslfjladljfdlsjfladjklfaslkdjflasdjlkfjal"
			},{
				title:"dfadsfads",
				content:"dfadsfads",
				content:"dsafjkldjfladsjlfjalsdfjladsjfljadslfjladsjfljadslfjlasdjfljasldfjlasdjfljadlsfjladjflajdslfjladsjfladjslfjaldsjfladjslfjaldjflajdlfjadlsjflasdjlfjsaldfjlsdjflajdslfjladljdfdslfjalsdjfladlasldjfladlfadlfldjflajdlkfdjfadsjlfajkdslfladsjkfldajlfladjfljadslfjladljfdlsjfladjklfaslkdjflasdjlkfjal"
			},{
				title:"dfadsfads",
				content:"dfadsfads",
				content:"dsafjkldjfladsjlfjalsdfjladsjfljadslfjladsjfljadslfjlasdjfljasldfjlasdjfljadlsfjladjflajdslfjladsjfladjslfjaldsjfladjslfjaldjflajdlfjadlsjflasdjlfjsaldfjlsdjflajdslfjladljdfdslfjalsdjfladlasldjfladlfadlfldjflajdlkfdjfadsjlfajkdslfladsjkfldajlfladjfljadslfjladljfdlsjfladjklfaslkdjflasdjlkfjal"
			},{
				title:"dfadsfads",
				content:"dfadsfads",
				content:"dsafjkldjfladsjlfjalsdfjladsjfljadslfjladsjfljadslfjlasdjfljasldfjlasdjfljadlsfjladjflajdslfjladsjfladjslfjaldsjfladjslfjaldjflajdlfjadlsjflasdjlfjsaldfjlsdjflajdslfjladljdfdslfjalsdjfladlasldjfladlfadlfldjflajdlkfdjfadsjlfajkdslfladsjkfldajlfladjfljadslfjladljfdlsjfladjklfaslkdjflasdjlkfjal"
			},{
				title:"dfadsfads",
				content:"dfadsfads",
				content:"dsafjkldjfladsjlfjalsdfjladsjfljadslfjladsjfljadslfjlasdjfljasldfjlasdjfljadlsfjladjflajdslfjladsjfladjslfjaldsjfladjslfjaldjflajdlfjadlsjflasdjlfjsaldfjlsdjflajdslfjladljdfdslfjalsdjfladlasldjfladlfadlfldjflajdlkfdjfadsjlfajkdslfladsjkfldajlfladjfljadslfjladljfdlsjfladjklfaslkdjflasdjlkfjal"
			},{
				title:"dfadsfads",
				content:"dfadsfads",
				content:"dsafjkldjfladsjlfjalsdfjladsjfljadslfjladsjfljadslfjlasdjfljasldfjlasdjfljadlsfjladjflajdslfjladsjfladjslfjaldsjfladjslfjaldjflajdlfjadlsjflasdjlfjsaldfjlsdjflajdslfjladljdfdslfjalsdjfladlasldjfladlfadlfldjflajdlkfdjfadsjlfajkdslfladsjkfldajlfladjfljadslfjladljfdlsjfladjklfaslkdjflasdjlkfjal"
			},{
				title:"dfadsfads",
				content:"dfadsfads",
				content:"dsafjkldjfladsjlfjalsdfjladsjfljadslfjladsjfljadslfjlasdjfljasldfjlasdjfljadlsfjladjflajdslfjladsjfladjslfjaldsjfladjslfjaldjflajdlfjadlsjflasdjlfjsaldfjlsdjflajdslfjladljdfdslfjalsdjfladlasldjfladlfadlfldjflajdlkfdjfadsjlfajkdslfladsjkfldajlfladjfljadslfjladljfdlsjfladjklfaslkdjflasdjlkfjal"
			},{
				title:"dfadsfads",
				content:"dfadsfads",
				content:"dsafjkldjfladsjlfjalsdfjladsjfljadslfjladsjfljadslfjlasdjfljasldfjlasdjfljadlsfjladjflajdslfjladsjfladjslfjaldsjfladjslfjaldjflajdlfjadlsjflasdjlfjsaldfjlsdjflajdslfjladljdfdslfjalsdjfladlasldjfladlfadlfldjflajdlkfdjfadsjlfajkdslfladsjkfldajlfladjfljadslfjladljfdlsjfladjklfaslkdjflasdjlkfjal"
			},{
				title:"dfadsfads",
				content:"dfadsfads",
				content:"dsafjkldjfladsjlfjalsdfjladsjfljadslfjladsjfljadslfjlasdjfljasldfjlasdjfljadlsfjladjflajdslfjladsjfladjslfjaldsjfladjslfjaldjflajdlfjadlsjflasdjlfjsaldfjlsdjflajdslfjladljdfdslfjalsdjfladlasldjfladlfadlfldjflajdlkfdjfadsjlfajkdslfladsjkfldajlfladjfljadslfjladljfdlsjfladjklfaslkdjflasdjlkfjal"
			}],
        	currentPage: 4,


			MsgType:"日志",
			username:"lph",
			isAnnorce:false,
			isLog:false,
			isUser:true,
			content:"zzx手动dsdfasjdkfjalsjdlkfjaklsdjfjklahkdjfhakhdklfhasklhdfklahlkhdfklahfklahldhflksahfdlkahdkljahjklhsdjfaljdlfjalsjdlfjlasjdlkfjkladjlfjlasdjlkfjslakjdlkfjaklsdjklfjlkdsajklfjakljfkljaslkdjflkjaskldjfklasjldkjflkajsdkl",
			date:"2019-10-1",
			title:"hello",
			msg: 'Welcome to Your Vue.js App',
			Table:[
				{type:'1',msg:'xxxx'},
				{type:'2',msg:'xx'},
				{type:'3',msg:'xy'}
			]
      }
    },
    methods: {
      	goBack() {
        	console.log('go back');
		},
		handleSizeChange(val) {
        	console.log(`每页 ${val} 条`);
      	},
      	handleCurrentChange(val) {
        	console.log(`当前页: ${val}`);
     	}  
    }
  }
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.search {
    position: absolute;
    width: 100%;
	height: 100%;
}
.header {
    /* background-color: #276E51; */
    background-image: url(~@/assets/bg2.png);
    background-size: 100% 100%;
    background-repeat: no-repeat;
    height: 100px;
    color: #fff;
    top: 0;
}
.system {
    position: absolute;
    font-size: 36px;
    top: 20px;
    margin-left: 50px;
}
.search_bar{
	position: relative;
	height: 80px;
	box-shadow: 0 2px 4px rgba(0, 0, 0, .12), 0 0 6px rgba(0, 0, 0, .04)
}
.search_content{
	position: relative;
	width: 700px;
	top: 20px;
	left: 140px;
}
.search_btn{
	position: relative;
	top: 20px;
	left: 150px;
}
.main_content{
	margin-top: 40px;
	margin-left: 80px;
	height: 80%;
}
.right{
	float: right;
}
.search_result{
	float: left;
	width: 65%;
	padding-right: 60px;
	padding-left: 60px;
	padding-bottom: 60px;
	/* background-color: hotpink; */
	box-shadow: 0 2px 12px 0 rgba(0, 0, 0, 0.1)
}
.result{
	margin-top: 20px;
}
.title{
	font-size: 30px;
	word-wrap: break-word;
	word-break: break-all;
	text-decoration: underline;
	/* background-color:greenyellow; */
}
.section_content{
	font-size: 20px;
	word-wrap: break-word;
	word-break: break-all;
	/* background-color: hotpink; */
	/* height: 100px; */
}
.page{
	margin-top: 30px;
}
h1,
h2 {
	font-weight: normal;
}

ul {
	list-style-type: none;
	padding: 0;
}

li {
	display: inline-block;
	margin: 0 10px;
}

a {
	color: #42b983;
}

.center {
	margin-left: 500px;
	margin-top: 50px;
}

.pagination {
	margin-top: 10px;
	text-align: center;
}
.show{
    width: 500px;
    height: 500px;
  
    float: right;
    box-shadow: 0 2px 4px rgba(0, 0, 0, .12), 0 0 6px rgba(0, 0, 0, .04)
}
.date{
	float: right;
}
.content{
	margin-top:5px;
	margin-left: 30px;
	word-wrap: break-word;
	word-break: break-all;
}
h3{
  	margin-left: 5px;
}
.text {
	font-size: 14px;
}

.item {
	margin-bottom: 18px;
}

.clearfix:before,
.clearfix:after {
	display: table;
	content: "";
}
.clearfix:after {
	clear: both
}

.box-card {
	width: 480px;
	float:right;
}
</style>
