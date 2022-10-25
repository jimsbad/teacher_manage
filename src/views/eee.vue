<template>
    <div style="padding: 10px">
        <div style="margin: 10px 0">
            <el-input v-model="input" placeholder="请输入内容" style="width: 20%"></el-input>
            <el-button type="primary">搜索</el-button>
        </div>
 <el-table :data="tableData" border style="width: 100%">
    <el-table-column prop="term" label="教师工号" />
    <el-table-column prop="courseNum" label="教学班号" />
    <el-table-column prop="courseName" label="学期" />
    <el-table-column prop="courseType" label="应到人数" />
    <el-table-column prop="classNum" label="到课人数" />
    <el-table-column prop="credit" label="迟到人数" />
    <el-table-column prop="planHours" label="早退人数" />
    <el-table-column prop="classWeek" label="前排落座率" />
    <el-table-column prop="classSection" label="专注人数" />
  </el-table>
    </div>
</template>


<script>


export default {
    name: 'eee',
    components: {

    },


}
</script>