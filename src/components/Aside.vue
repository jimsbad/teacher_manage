`


.
<template>
  <div>
    <el-menu
        style="width: 200px; min-height: calc(100vh - 50px)"
        default-active="course"
        router
        class="el-menu-vertical-demo"

    >
      <el-sub-menu index="1">

        <template #title>
          <el-icon>
            <location/>
          </el-icon>
          <span>教学过程</span>
        </template>

        <el-menu-item index="course">
          <el-icon>
            <icon-menu/>
          </el-icon>
          <span>理论实践课程</span>
        </el-menu-item>

        <el-menu-item index="bbb">
          <el-icon>
            <icon-menu/>
          </el-icon>
          <span>其他教学</span>
        </el-menu-item>
        <el-menu-item index="ccc">
          <el-icon>
            <icon-menu/>
          </el-icon>
          <span>学生评教</span>
        </el-menu-item>
        <el-menu-item index="ddd">
          <el-icon>
            <icon-menu/>
          </el-icon>
          <span>听课评教</span>
        </el-menu-item>
        <el-menu-item index="eee">
          <el-icon>
            <icon-menu/>
          </el-icon>
          <span>课堂监控</span>
        </el-menu-item>
      </el-sub-menu>
      <el-sub-menu index="2">
        <template #title>
          <el-icon>
            <location/>
          </el-icon>
          <span>教学发展</span>
        </template>
        <el-menu-item index="ggg">
          <el-icon>
            <icon-menu/>
          </el-icon>
          <span>参与教学团队</span>
        </el-menu-item>
        <el-menu-item index="fff">
          <el-icon>
            <icon-menu/>
          </el-icon>
          <span>参加培训</span>
        </el-menu-item>
      </el-sub-menu>
      <el-sub-menu index="3">
        <template #title>
          <el-icon>
            <location/>
          </el-icon>
          <span>指导能力</span>
        </template>
        <el-menu-item index="compete">
          <el-icon>
            <icon-menu/>
          </el-icon>
          <span>指导学生竞赛</span>
        </el-menu-item>
        <el-menu-item index="project">
          <el-icon>
            <icon-menu/>
          </el-icon>
          <span>指导学生项目</span>
        </el-menu-item>
        <el-menu-item index="paper">
          <el-icon>
            <icon-menu/>
          </el-icon>
          <span>指导学生论文</span>
        </el-menu-item>
        <el-menu-item index="property">
          <el-icon>
            <icon-menu/>
          </el-icon>
          <span>指导学生知识产权</span>
        </el-menu-item>
      </el-sub-menu>
    </el-menu>
  </div>
</template>

<script>
export default {
  name: "Aside"
}
</script>

<style scoped>

</style>