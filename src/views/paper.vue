<template>

  <div style="padding: 10px">
    <div style="margin: 10px 0">
      <el-button type="primary" @click="add">新增</el-button>
      <el-button type="primary" @click="exp">导出</el-button>
      <el-button type="primary" @click="reset">重置</el-button>
      <el-button type="primary" @click="download">下载模板</el-button>
      <el-button type="primary" @click="post">点击上传</el-button>
      <input type="file" @change="fileValueChange2()" ref="uploadFile2" enctype="multipart/form-data" id="import_btn"
             style="display:none;">


    </div>


    <div style="margin: 10px 0">
      <el-input v-model="courseID" placeholder="请输入内容" style="width: 20%"></el-input>
      <el-button type="primary" @click="search">搜索</el-button>
    </div>
    <!---->


    <el-table :data="tableData1" border style="width: 100%">
      <el-table-column prop="teacher_id" label="老师工号"/>
      <el-table-column prop="title" label="论文题目"/>
      <el-table-column prop="company" label="所在单位"/>
      <el-table-column prop="stu_message" label="学生列表"/>
      <el-table-column prop="paper_name" label="期刊名称"/>
      <el-table-column prop="paper_level" label="级别"/>
      <el-table-column prop="journal_volume" label="期刊卷次"/>
      <el-table-column prop="paper_time" label="获奖时间"/>
      <el-table-column prop="remarks" label="备注"/>
      <el-table-column prop="support_materials" label="材料"/>
      <el-table-column fixed="right" label="操作" width="100">
        <template #default="scope">
          <el-button @click="handleEdit(scope.row,scope.row.courseID)" type="text" size="small">编辑</el-button>
          <el-button type="text" size="small" @click="handleDelete(scope.row.courseID)">删除</el-button>
        </template>
      </el-table-column>
    </el-table>
    <el-dialog title="导入学生" v-model="importDialogVisible" width="45%">
      <input ref="file" type="file" accept=".xlsx,.xls" style="display: none;" @change="uploadFile">
      <el-button type="primary" icon="el-icon-upload" @click="clickFile">选择文件</el-button>

    </el-dialog>

    <!-- 弹窗 -->
    <el-dialog title="提示" v-model="dialogVisible" width="60%">
      <el-form :model="form" label-width="120px">
        <el-row>
          <el-col :span="12">
            <el-form-item label="老师工号">
              <el-input v-model="form.teacher_id" style="width: 30%"></el-input>
            </el-form-item>
          </el-col>
          <el-col :span="12">
            <el-form-item label="论文题目">
              <el-input v-model="form.title" style="width: 30%"></el-input>
            </el-form-item>
          </el-col>
          <el-col :span="12">
            <el-form-item label="所在单位">
              <el-input v-model="form.company" style="width: 30%"></el-input>
            </el-form-item>
          </el-col>
          <el-col :span="12">
            <el-form-item label="学生列表">
              <el-input v-model="form.stu_message" style="width: 30%"></el-input>
            </el-form-item>
          </el-col>
          <el-col :span="12">
            <el-form-item label="期刊名称">
              <el-input v-model="form.paper_name" style="width: 30%"></el-input>
            </el-form-item>
          </el-col>
          <el-col :span="12">
            <el-form-item label="级别">
              <el-input v-model="form.paper_level" style="width: 30%"></el-input>
            </el-form-item>
          </el-col>
        </el-row>
        
        <el-row>
          <el-col :span="12">
            <el-form-item label="期刊卷次">
              <el-input v-model="form.journal_volume" style="width: 30%"></el-input>
            </el-form-item>
          </el-col>
          <el-col :span="12">
            <el-form-item label="备注">
              <el-input v-model="form.remarks" style="width: 30%"></el-input>
            </el-form-item>
          </el-col>
          <el-col :span="12">
            <el-form-item label="材料">
              <el-input v-model="form.support_materials" style="width: 30%"></el-input>
            </el-form-item>
          </el-col>
          <el-col :span="12">
            <el-form-item label="学生列表">
              <el-input v-model="form.stu_message" style="width: 30%" ></el-input>
              <el-button type="primary">新增</el-button>
            </el-form-item>
          </el-col>
          <el-col :span="12">
            <el-form-item label="老师工号">
              <el-input v-model="form.team_id" style="width: 30%"></el-input>
              <el-button type="primary">新增</el-button>
            </el-form-item>
          </el-col>
        </el-row>
      </el-form>


      <template #footer>
                <span class="dialog-footer">
                  <el-button @click="dialogVisible = false">取 消</el-button>
                  <el-button type="primary" @click="save" dialogVisible=false>确 定</el-button>
                </span>
      </template>
    </el-dialog>
  </div>
</template>


<script>


// import request from "@/utils/request";
/* import { id } from 'element-plus/lib/locale'; */

import axios from "axios";
import {importExcel} from "@/utils/request";
// import {FileSaver} from "file-saver";
// import {XLSX} from "xlsx";

export default {
  name: 'paper',
  components: {},
  data() {
    return {
      fileList: [], //上传文件列表
      tableHead: [], //表头
      tableData: [], // 表数据
      form: {},
      dialogVisible: false,
      courseID: "",
      id: "",
      tableData1: [],
      importDialogVisible: false,
      loading: false
    }
  },
  created() {
    this.load()
  },

  methods: {
    load() {
      axios.get("http://localhost:8080/paper/", {}).then(res => {
        console.log(res)
        this.tableData1 = res.data
      })
    },
    post() {
      this.$refs.uploadFile2.click()
      // axios.post("http://localhost:8080/paper/importExcel",{})
      let fd = new FormData();
      fd.append("name", this.name);
      this.fileList.forEach(item => {
        //文件信息中raw才是真的文件
        fd.append("files", item.raw);
        //console.log(item.raw)
      })
      this.$axios.post('/http://localhost:8080/paper/importExcel', fd).then(res => {
        if (res.data.code === 200) {
          //console.log(res);
          this.$message('上传成功')
        } else {
          this.$message('失败')
        }
      })
    },
    uploadFile2() {
      // 当点击button按钮后会触发此事件
      // 作用就是打开文件上传弹框
      this.$refs.uploadFile2.click()
    },
    fileValueChange2() {
      // 选中文件后，会触发input的change事件，即会进入此函数
      var formData = new FormData()
      // this.$refs.uploadFile2是vue中获取dom元素的方法
      // 通过files就可以拿到所有上传的文件，如果是多个文件循环即可
      formData.append('file', this.$refs.uploadFile2.files[0])
      // 必须设置请求类型
      //formData.append( 'type', "Blob");
      // 如果需要传id的情况下，参考下面代码
      //formData.append( 'id', this.id);
      // 配置完成后，只需要向后台传入formData 变量即可
      //multiple=”multiple  多文件可选
      // for(let i=0;i<deviceFile.length;i++){
      //     formData.append('file', deviceFile[i]);
      //   }
      let file = formData;
      this.loading = true
      //调用接口上传到后台
      importExcel(file).then(res => {
        if (res.data.status == 10000) {
          this.$message.success('success');
          //清空value值  解决无法上传相同名字文件的问题
          document.getElementById("import_btn").value = "";
        }
      }).catch((e) => {
        this.$message.error("excel上传失败，请重新上传");
        document.getElementById("import_btn").value = "";
      })
    },

    search() {
      axios.post("http://localhost:8080/course/getcourse", {"courseID": this.courseID}).then(res => {
        console.log(1)
        console.log(res)

        console.log(2)
        this.tableData = res.data
      })
    },

//       新增
    add() {
      this.dialogVisible = true
      this.form = {}
    },
// 确定
    save() {
      console.log(this.form)
      if (this.id !== 0) {
        axios.post("http://localhost:8080/paper/insert", this.form).then(res => {
          console.log(res)
          this.load()                   //更新数据
          this.dialogVisible = false   //关闭弹窗
        })
      }
    },
//编辑
    handleEdit(row, courseID) {
      this.form = JSON.parse(JSON.stringify(row))
      this.dialogVisible = true
      this.id = courseID

    },

    reset() {
      this.courseID = ""
      this.load
    },
//删除
    handleDelete(courseID) {
      axios.post("http://localhost:8080/course/delete", {
        "courseID": courseID
      }).then(res => {
        console.log(res)
        if (res.status == 200) {
          this.$message({
            type: "success",
            message: "删除成功"
          })
        } else {
          this.$message({
            type: "error",
            message: res.msg
          })
        }
        this.load()
      })
    },
    exp() {
      window.open("http://localhost:8080/paper/download")
    },
    download() {
      window.open("http://localhost:8080/paper/downloadTemplate")
    },
    handleFileUploadSuccess(res) {
      this.$message.success("上传成功")
      this.load()
    },
    preview(url) {
      window.open('https://file.keking.cn/onlinePreview?url=' + encodeURIComponent(window.btoa((url))))
    },

  }
}
</script>