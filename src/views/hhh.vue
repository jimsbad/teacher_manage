<template>
    <div style="padding: 10px">
        <div style="margin: 10px 0">
            <el-input v-model="input" placeholder="请输入内容" style="width: 20%"></el-input>
            <el-button type="primary">搜索</el-button>
        </div>
 <el-table :data="tableData" border style="width: 100%">
    <el-table-column prop="term" label="学期" />
    <el-table-column prop="courseNum" label="课程编号" />
    <el-table-column prop="courseName" label="课程名称" />
    <el-table-column prop="courseType" label="课程类型" />
    <el-table-column prop="classNum" label="班级编号" />
    <el-table-column prop="credit" label="学分" />
    <el-table-column prop="planHours" label="计划学时数" />
    <el-table-column prop="classWeek" label="开课周" />
    <el-table-column prop="classSection" label="开课节" />
    <el-table-column prop="classroom" label="占用教室" />
    <el-table-column prop="genreNum" label="课程类别系数" />
    <el-table-column prop="studentNum" label="学生人数" />
    <el-table-column prop="classSize" label="教学班规模" />
    <el-table-column prop="examination" label="考核方式" />
    <el-table-column prop="actualHours" label="实际课堂教学时数" />
    <el-table-column prop="remark" label="备注" />
  </el-table>
    </div>
</template>

<script>


export default {
    name: 'hhh',
    components: {

    },
    data() {
        return {
            tableData: []
        }
    },
    methods: {
        
    }

}
</script>