<template>
  <div>
       <el-page-header @back="goBack" content="日志详情">
       </el-page-header>
  <div class="center">
 
    <el-table :data="tableData" border style="width: 900px;">
      <el-table-column prop="date" label="日期" width="180">
      </el-table-column>
      <el-table-column prop="address" label="信息">
      </el-table-column>
    </el-table>
  </div>
     <div class="pagination">
       <el-pagination @size-change="handleSizeChange" @current-change="handleCurrentChange" :current-page="currentPage4"
         :page-sizes="[5, 10, 20, 400]" :page-size="100" layout="total, sizes, prev, pager, next, jumper"
         :total="400">
       </el-pagination>
     </div>
    </div>
  
</template>

<script>
export default {
  name: 'HelloWorld',
  data () {
    return {
      tableData: [{
      date: '2016-05-02',
      name: '王小虎',
      address: '上海市普陀区金沙江路 1518 弄'
      }, {
      date: '2016-05-04',
      name: '王小虎',
      address: '上海市普陀区金沙江路 1517 弄'
      }, {
      date: '2016-05-01',
      name: '王小虎',
      address: '上海市普陀区金沙江路 1519 弄'
      }, {
      date: '2016-05-03',
      name: '王小虎',
      address: '上海市普陀区金沙江路 1516 弄'
      }],
      msg: 'Welcome to Your Vue.js App'
    }
  },
   methods: {
   goBack() {
   console.log('go back');
   }
   }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h1, h2 {
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
.center{
  margin-left: 500px;
  margin-top:50px;
}
.pagination{
  margin-top: 10px;
  text-align: center;
}
</style>
