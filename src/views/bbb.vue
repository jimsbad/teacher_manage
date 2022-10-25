<template>
    <div style="padding: 10px">
        <div style="margin: 10px 0">
            <el-input v-model="input" placeholder="请输入内容" style="width: 20%"></el-input>
            <el-button type="primary">搜索</el-button>
        </div>
 <el-table :data="tableData" border style="width: 100%">
    <el-table-column prop="term" label="学年" />
    <el-table-column prop="courseNum" label="学期" />
    <el-table-column prop="courseName" label="其他教学内容" />
    <el-table-column prop="courseType" label="运动天数" />
    <el-table-column prop="classNum" label="学生人数" />
    <el-table-column prop="credit" label="标准课时数" />
    <el-table-column prop="planHours" label="笔记天数" />
    <el-table-column prop="classWeek" label="备注" />

  </el-table>
    </div>
</template>


<script>


export default {
    name: 'bbb',
    components: {

    },


}
</script>