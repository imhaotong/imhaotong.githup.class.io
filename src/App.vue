<template>
  <div id="app">
    <div id="nav">
    	
    	 <el-table
    :data="tableData"
    border
    style="width: 100%">
    <el-table-column
      fixed
      prop="c1"
      label="week"
      width="150">
    </el-table-column>
    <el-table-column
      prop="c2"
      label="one"
      width="120">
    </el-table-column>
    <el-table-column
      prop="c3"
      label="two"
      width="120">
    </el-table-column>
    <el-table-column
      prop="c4"
      label="three"
      width="120">
    </el-table-column>
    <el-table-column
      prop="c5"
      label="four"
      width="120">
    </el-table-column>
    <el-table-column
      prop="c6"
      label="five"
      width="120">
    </el-table-column>
      <el-table-column
      prop="c7"
      label="six"
      width="120">
       </el-table-column>
         <el-table-column
      prop="c8"
      label="seven"
      width="120">
       </el-table-column>
         <el-table-column
      prop="c9"
      label="eight"
      width="120">
       </el-table-column>
    <el-table-column
      fixed="right"
      label="操作"
      width="100">
      <template slot-scope="scope">
      <el-button type="text" size="small">编辑</el-button>
      </template>
    </el-table-column>
  </el-table>

    	
     
    </div>
    <router-view/>
  </div>
</template>

<script>
  export default {
   

    data() {
      return {
        tableData: [],
      }
    },
       created(){
     this.$http.get('http://localhost:8002/sel').then(e=>this.tableData=e.body)
      },
      methods:{
      	fz(){
      	this.$http.post('http://localhost:8002/sel',{id:this.$route.params.id},{emulateJSON:true}).then(e=>this.tableData=e.body)
      },
       submit(){
      	this.$http.post('http://localhost:8002/add',this.form,{emulateJSON:true}).then((e)=>{
      	this.fz()
      		this.form={}
      	})
      }	
      }
    
  }
</script>


<style>
	*{
		text-align: center;
	}
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}
#nav {
  padding: 30px;
}

#nav a {
  font-weight: bold;
  color: #2c3e50;
}

#nav a.router-link-exact-active {
  color: #42b983;
}

</style>

