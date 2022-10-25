<template>
    <div style="padding: 10px">
        <div style="margin: 10px 0">
            <el-input v-model="input" placeholder="请输入内容" style="width: 20%"></el-input>
            <el-button type="primary">搜索</el-button>
        </div>
 <el-table :data="tableData" border style="width: 100%">
    <el-table-column prop="term" label="学期" />
    <el-table-column prop="courseNum" label="教学班号" />
    <el-table-column prop="courseName" label="开课学院" />
    <el-table-column prop="courseType" label="课程名称" />
    <el-table-column prop="classNum" label="听课日期" />
    <el-table-column prop="credit" label="任课老师工号" />
    <el-table-column prop="planHours" label="任课老师姓名" />
    <el-table-column prop="classWeek" label="任课老师职称" />
    <el-table-column prop="classSection" label="听课老师工号" />
    <el-table-column prop="classroom" label="听课老师姓名" />
    <el-table-column prop="genreNum" label="听课老师职称" />
    <el-table-column prop="studentNum" label="听课类型" />
    <el-table-column prop="classSize" label="听课分数" />
    <el-table-column prop="examination" label="听课评价" />
    <el-table-column prop="remark" label="备注" />
  </el-table>
    </div>
</template>


<script>


export default {
    name: 'ddd',
    components: {

    },


}
</script>