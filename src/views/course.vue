<template>
    <div style="padding: 10px">
        <div style="margin: 10px 0">
            <el-button type="primary" @click="add">新增</el-button>
            <el-button type="primary" @click="exp">导出</el-button>
            <el-button type="primary" @click="reset">重置</el-button>
        </div>

<!--         <div class="mt-4" style="margin: 10px 0">
            <el-input v-model="courseID" placeholder="请输入内容" style="width: 30%">
           <template #prepend>
               <el-select v-model="select" placeholder="选择类型" style="width: 100px">
               <el-option label="学期" value="1" />
               <el-option label="课程编号" value="2" />
               <el-option label="课程名称" value="3" />
               </el-select>
           </template>
            <template #append>
                <el-button type="primary">搜索</el-button>
            </template>
            </el-input>
        </div> -->

        <div style="margin: 10px 0">
            <el-input v-model="courseID" placeholder="请输入内容" style="width: 20%"></el-input>
            <el-button type="primary" @click="search">搜索</el-button>
        </div>

<!--         <div style="margin: 10px 0">
            <el-input v-model="courseID" placeholder="请输入内容" style="width: 20%"></el-input>
            <el-button type="primary" @click="load">搜索</el-button>
        </div> -->

        <el-table :data="tableData" border style="width: 100%">
            <el-table-column prop="term" label="学期" />
            <el-table-column prop="courseID" label="课程编号" />
            <el-table-column prop="courseName" label="课程名称" />
            <el-table-column prop="courseType" label="课程类型" />
            <el-table-column prop="classID" label="班级编号" />
            <el-table-column prop="credit" label="学分" />
            <el-table-column prop="planHours" label="计划学时数" />
            <el-table-column prop="classWeek" label="开课周" />
            <el-table-column prop="classSection" label="开课节" />
            <el-table-column prop="classroom" label="占用教室" />
            <el-table-column prop="genreNum" label="课程类别系数" />
            <el-table-column prop="studentNum" label="学生人数" />
            <el-table-column prop="classsize" label="教学班规模" />
            <el-table-column prop="examination" label="考核方式" />
            <el-table-column prop="whetherOnline" label="是否为网络教学" />
            <el-table-column prop="onlinePlatform" label="网络教学平台" />
            <el-table-column prop="actualHours" label="实际课堂教学时数" />
            <el-table-column prop="remark" label="备注" />
            <el-table-column fixed="right" label="操作" width="100">
                <template #default="scope">
                    <el-button @click="handleEdit(scope.row)" type="text" size="small"
                      >编辑</el-button
                    >
                    <el-button type="text" size="small" @click="handleDelete(scope.row.courseID)">删除</el-button>
                  </template>
            </el-table-column>
        </el-table>
        
        <!-- 弹窗 -->
        <el-dialog title="提示" v-model="dialogVisible" width="30%">
            <el-form :model="form" label-width="120px">
                <el-form-item label="学期">
                    <el-input v-model="form.term" style="width: 80%"></el-input>
                </el-form-item>
            </el-form>
            <el-form :model="form" label-width="120px">
                <el-form-item label="课程编号">
                    <el-input v-model="form.courseID" style="width: 80%"></el-input>
                </el-form-item>
            </el-form>
            <el-form :model="form" label-width="120px">
                <el-form-item label="课程名称">
                    <el-input v-model="form.courseName" style="width: 80%"></el-input>
                </el-form-item>
            </el-form>
            <el-form :model="form" label-width="120px">
                <el-form-item label="课程类型">
                    <el-input v-model="form.courseType" style="width: 80%"></el-input>
                </el-form-item>
            </el-form>
            <el-form :model="form" label-width="120px">
                <el-form-item label="班级编号">
                    <el-input v-model="form.classID" style="width: 80%"></el-input>
                </el-form-item>
            </el-form>
            <el-form :model="form" label-width="120px">
                <el-form-item label="学分">
                    <el-input v-model="form.credit" style="width: 80%"></el-input>
                </el-form-item>
            </el-form>
            <el-form :model="form" label-width="120px">
                <el-form-item label="计划学时数">
                    <el-input v-model="form.planHours" style="width: 80%"></el-input>
                </el-form-item>
            </el-form>
            <el-form :model="form" label-width="120px">
                <el-form-item label="开课周">
                    <el-input v-model="form.classWeek" style="width: 80%"></el-input>
                </el-form-item>
            </el-form>
            <el-form :model="form" label-width="120px">
                <el-form-item label="开课节">
                    <el-input v-model="form.classSection" style="width: 80%"></el-input>
                </el-form-item>
            </el-form>
            <el-form :model="form" label-width="120px">
                <el-form-item label="占用教室">
                    <el-input v-model="form.classroom" style="width: 80%"></el-input>
                </el-form-item>
            </el-form>
            <el-form :model="form" label-width="120px">
                <el-form-item label="课程类别系数">
                    <el-input v-model="form.genreNum" style="width: 80%"></el-input>
                </el-form-item>
            </el-form>
            <el-form :model="form" label-width="120px">
                <el-form-item label="学生人数">
                    <el-input v-model="form.studentNum" style="width: 80%"></el-input>
                </el-form-item>
            </el-form>
            <el-form :model="form" label-width="120px">
                <el-form-item label="教学班规模">
                    <el-input v-model="form.classsize" style="width: 80%"></el-input>
                </el-form-item>
            </el-form>
            <el-form :model="form" label-width="120px">
                <el-form-item label="考核方式">
                    <el-input v-model="form.examination" style="width: 80%"></el-input>
                </el-form-item>
            </el-form>
            <el-form :model="form" label-width="120px">
                <el-form-item label="是否为网络教学">
                    <el-input v-model="form.whetherOnline" style="width: 80%"></el-input>
                </el-form-item>
            </el-form>
            <el-form :model="form" label-width="120px">
                <el-form-item label="网络教学平台">
                    <el-input v-model="form.onlinePlatform" style="width: 80%"></el-input>
                </el-form-item>
            </el-form>
            <el-form :model="form" label-width="120px">
                <el-form-item label="实际课堂教学时数">
                    <el-input v-model="form.actualHours" style="width: 80%"></el-input>
                </el-form-item>
            </el-form>
            <el-form :model="form" label-width="120px">
                <el-form-item label="备注">
                    <el-input v-model="form.remark" style="width: 80%"></el-input>
                </el-form-item>
            </el-form>
            <template #footer>
                <span class="dialog-footer">
                  <el-button @click="dialogVisible = false">取 消</el-button>
                  <el-button type="primary" @click="save" dialogVisible = false>确 定</el-button>
                </span>
            </template>
        </el-dialog>
    </div>
</template>




<script>


// import request from "@/utils/request";
/* import { id } from 'element-plus/lib/locale'; */

import axios from "axios";


export default {
    name: 'course',
    components: {

    },
    data() {
        return {

            form: {},
            dialogVisible: false,
            courseID: " ",
            tableData: [],
      }
    },
    created() {
        this.load()
    },
    methods: {
        load() {
            axios.get("http://localhost:8080/course",{
/*                 params: {
                    courseID: this.courseID
                } */
            }).then(res => {
                console.log(res)
                this.tableData = res.data
            })
        },

        search() {
            axios.post("http://localhost:8080/course/getcourse",this.courseID).then(res => {
                this.load()
            })
        },

//       新增  
         add(){
            this.dialogVisible = true
            this.form = {}
        },
// 确定
        save(){
            if (this.form.id) {
                 axios.post("http://localhost:8080/course/update",this.form).then(res => {
                    console.log(res)
/*                     if (res.code === '0'){
                        this.$message({
                            type: "success",
                            message: "更新成功"
                        })
                    } else {
                        this.$message({
                            type: "error",
                            message: res.msg
                        })
                    } */
                    this.load()                   //更新数据
                    this.dialogVisible = false   //关闭弹窗
                })
            } else {    
                axios.post("http://localhost:8080/course/insert",this.form).then(res => {
                    console.log(res)
/*                     if (res.code === '0'){
                        this.$message({
                            type: "success",
                            message: "新增成功"
                        })
                    } else {
                        this.$message({
                            type: "error",
                            message: res.msg
                        })
                    } */
                    this.load()                   //更新数据
                    this.dialogVisible = false   //关闭弹窗
                })
            }
        },
//编辑
        handleEdit(row) {
            this.form = JSON.parse(JSON.stringify(row))
            this.dialogVisible = true
        },

        reset() {
            this.courseID = ""
            this.load
        },
//删除
        handleDelete(courseID) {
            axios.post("http://localhost:8080/course/delete",courseID).then(res => {
                // if (res.code === '0'){
                //     this.$message({
                //         type: "success",
                //         message: "删除成功"
                //     })
                // } else {
                //     this.$message({
                //         type: "error",
                //         message: res.msg
                //         })
                // }
                this.load()
            })
        },
      exp(){
          window.open("http://localhost:8080/course/download")
      }

    }

}
</script>