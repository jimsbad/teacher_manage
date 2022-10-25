<template>
    <div style="padding: 10px">
        <div style="margin: 10px 0">
            <el-input v-model="input" placeholder="请输入内容" style="width: 20%"></el-input>
            <el-button type="primary">搜索</el-button>
        </div>
 <el-table :data="tableData" border style="width: 100%">
    <el-table-column prop="term" label="教师工号" />
    <el-table-column prop="courseNum" label="姓名" />
    <el-table-column prop="courseName" label="部门" />
    <el-table-column prop="courseType" label="职称" />
    <el-table-column prop="classNum" label="校外培训次数" />
    <el-table-column prop="credit" label="校内培训次数" />
    <el-table-column prop="planHours" label="培训总学时" />
  </el-table>
    </div>
</template>


<script>


export default {
    name: 'fff',
    components: {

    },


}
</script>