<template>
    <div style="padding: 10px">
        <div style="margin: 10px 0">
            <el-input v-model="input" placeholder="请输入内容" style="width: 20%"></el-input>
            <el-button type="primary">搜索</el-button>
        </div>
        <el-table :data="tableData" border style="width: 100%">
        <el-table-column prop="term" label="教师工号" />
        <el-table-column prop="courseNum" label="学年" />
        <el-table-column prop="courseName" label="学期" />
        <el-table-column prop="courseType" label="评价人数" />
        <el-table-column prop="classNum" label="评价得分" />
        <el-table-column prop="credit" label="学院排名" />
        <el-table-column prop="planHours" label="学院总教师数" />
        <el-table-column prop="classWeek" label="备注" />
        </el-table>
    </div>

    <div style="padding: 10px">
        <br>
        <br>
        <br>
        <el-table :data="tableData" border style="width: 100%">
        <el-table-column prop="term" label="教师工号" />
        <el-table-column prop="courseNum" label="学年" />
        <el-table-column prop="courseName" label="学期" />
        <el-table-column prop="courseType" label="课程编号" />
        <el-table-column prop="classNum" label="课程名称" />
        <el-table-column prop="credit" label="评价人数" />
        <el-table-column prop="planHours" label="评价类型" />
        <el-table-column prop="classWeek" label="评价名称" />
        <el-table-column prop="classWeek" label="评价分数" />
        <el-table-column prop="classWeek" label="评价内容" />
        </el-table>
    </div>
</template>


<script>


export default {
    name: 'ccc',
    components: {

    },


}
</script>