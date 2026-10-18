<template>
  <el-container>
    <el-header style="font-size: 40px; background-color: rgb(238, 241, 246)"
      >Quiz后台管理</el-header
    >
    <el-container>
      <el-aside width="200px" style="background-color: rgb(238, 241, 246)">
        <el-menu :default-openeds="['1']">
          <el-submenu index="1">
            <template slot="title">
              <i class="el-icon-message"></i>系统信息管理
            </template>
            <el-menu-item index="1-1">
              <router-link to="/user">用户管理</router-link>
            </el-menu-item>
            <el-menu-item index="1-2">
              <router-link to="/question">题目管理</router-link>
            </el-menu-item>
          </el-submenu>
        </el-menu>
      </el-aside>

      <el-main>
        <!-- 用于查询的表单 -->
        <el-form :inline="true" :model="formInline" class="demo-form-inline">
          <el-form-item label="用户名">
            <el-input v-model="formInline.user" placeholder="用户名"></el-input>
          </el-form-item>
          <el-form-item>
            <el-button type="primary" @click="onSubmit">查询用户</el-button>
            <el-button type="success" @click="dialogFormVisible = true"
              >添加用户</el-button
            >
          </el-form-item>
        </el-form>

        <!-- 表格 -->
        <el-table :data="tableData" style="width: 100%">
          <el-table-column prop="date" label="日期" width="180">
          </el-table-column>
          <el-table-column prop="name" label="用户名" width="180">
            <template slot-scope="scope">
              <el-button type="text">{{ scope.row.name }}</el-button>
            </template>
          </el-table-column>
          <el-table-column prop="password" label="密码"> </el-table-column>
          <el-table-column label="操作">
            <template slot-scope="scope">
              <el-button size="mini" @click="handleEdit(scope.row)">编辑</el-button>
              <el-button
                size="mini"
                type="danger"
                @click="handleDelete(scope.row)"
                >删除</el-button
              >
            </template>
          </el-table-column>
        </el-table>

        <!-- 分页条 -->
        <el-pagination
          background
          layout="prev, pager, next"
          :total="1000"
        >
        </el-pagination>

        <!-- 弹出的添加用户的对话框 -->
        <el-dialog title="新用户" :visible.sync="dialogFormVisible">
          <el-form :model="form">
            <el-form-item label="用户名" :label-width="formLabelWidth">
              <el-input v-model="form.name" autocomplete="off"></el-input>
            </el-form-item>
            <el-form-item label="初始密码" :label-width="formLabelWidth">
              <el-input v-model="form.password" autocomplete="off"></el-input>
            </el-form-item>
            <el-form-item label="确认密码" :label-width="formLabelWidth">
              <el-input
                v-model="form.confirmPassword"
                autocomplete="off"
              ></el-input>
            </el-form-item>
          </el-form>
          <div slot="footer" class="dialog-footer">
            <el-button @click="dialogFormVisible = false">取 消</el-button>
            <el-button type="primary" @click="dialogFormVisible = false"
              >确 定</el-button
            >
          </div>
        </el-dialog>
      </el-main>
    </el-container>
  </el-container>
</template>

<script>
export default {
  data() {
    return {
      dialogFormVisible: false,
      formLabelWidth: '120px',
      form: {
        name: '',
        password: '',
        confirmPassword: ''
      },
      formInline: {
        user: '',
        region: ''
      },
      tableData: [
        {
          date: '2016-05-02',
          name: '王小虎',
          password: '123456'
        },
        {
          date: '2016-05-04',
          name: '王小虎',
          password: '123456'
        },
        {
          date: '2016-05-01',
          name: '王小虎',
          password: '123456'
        },
        {
          date: '2016-05-03',
          name: '王小虎',
          password: '123456'
        }
      ]
    }
  },
  methods: {
    onSubmit() {
      console.log('submit!')
    },
    handleEdit(row) {
      console.log('edit', row)
    },
    handleDelete(row) {
      console.log('delete', row)
    }
  }
}
</script>

<style>
</style>
