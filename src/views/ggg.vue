<template>
  <el-table :data="tableData" style="width: 100%">
    <el-table-column type="expand">
      <template #default="props">
        <el-form label-position="left" inline class="demo-table-expand">
          <el-form-item label="教师工号">
            <span>{{ props.row.name }}</span>
          </el-form-item>
          <el-form-item label="团队类型">
            <span>{{ props.row.shop }}</span>
          </el-form-item>
          <el-form-item label="团队级别">
            <span>{{ props.row.id }}</span>
          </el-form-item>
          <el-form-item label="团队级别">
            <span>{{ props.row.shopId }}</span>
          </el-form-item>
          <el-form-item label="团队总人数">
            <span>{{ props.row.category }}</span>
          </el-form-item>
          <el-form-item label="佐证材料">
            <span>{{ props.row.address }}</span>
          </el-form-item>
          <el-form-item label="备注">
            <span>{{ props.row.desc }}</span>
          </el-form-item>
        </el-form>
      </template>
    </el-table-column>
    <el-table-column label="学期" prop="id"> </el-table-column>
    <el-table-column label="团队名称" prop="name"> </el-table-column>
    <el-table-column label="团队排名" prop="desc"> </el-table-column>
  </el-table>
</template>

<script>
  export default {
    name: 'ggg',
    components: {

    },
    data() {
      return {
        tableData: [

          {
            id: '11',
            name: 'a',
            category: 'aaa',
            desc: 'ddd',
            address: 'ss',
            shop: 'ff',
            shopId: 'ff',
          },
          {
            id: 'w',
            name: 'e',
            category: 's',
            desc: 't',
            address: 'xx',
            shop: 'aa',
            shopId: 'hh',
          },

        ],
      }
    },
  }
</script>
<style>
  .demo-table-expand {
    font-size: 0;
  }
  .demo-table-expand label {
    width: 90px;
    color: #99a9bf;
  }
  .demo-table-expand .el-form-item {
    margin-right: 0;
    margin-bottom: 0;
    width: 50%;
  }
</style>
