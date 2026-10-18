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
          <el-form-item label="题目">
            <el-input
              v-model="formInline.user"
              placeholder="题目关键词"
            ></el-input>
          </el-form-item>
          <el-form-item>
            <el-button type="success" @click="onSubmit">查询题目</el-button>
            <el-button type="success" @click="dialogFormVisible = true"
              >添加题目</el-button
            >
          </el-form-item>
        </el-form>

        <!-- 表格 -->
        <el-table :data="tableData" style="width: 100%">
          <el-table-column prop="id" label="序号" width="180">
          </el-table-column>
          <el-table-column prop="question" label="问题"> </el-table-column>
          <el-table-column prop="options" label="选项"> </el-table-column>
          <el-table-column prop="answer" label="答案"> </el-table-column>
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

        <!-- 弹出的添加题目的对话框 -->
        <el-dialog title="添加新题目" :visible.sync="dialogFormVisible">
          <el-form :model="form">
            <el-form-item label="题目" :label-width="formLabelWidth">
              <el-input v-model="form.title" autocomplete="off"></el-input>
            </el-form-item>
            <el-form-item label="问题内容" :label-width="formLabelWidth">
              <el-input v-model="form.question" autocomplete="off"></el-input>
            </el-form-item>
            <el-form-item label="选项A" :label-width="formLabelWidth">
              <el-input v-model="form.optionA" autocomplete="off"></el-input>
            </el-form-item>
            <el-form-item label="选项B" :label-width="formLabelWidth">
              <el-input v-model="form.optionB" autocomplete="off"></el-input>
            </el-form-item>
            <el-form-item label="选项C" :label-width="formLabelWidth">
              <el-input v-model="form.optionC" autocomplete="off"></el-input>
            </el-form-item>
            <el-form-item label="选项D" :label-width="formLabelWidth">
              <el-input v-model="form.optionD" autocomplete="off"></el-input>
            </el-form-item>
            <el-form-item label="答案" :label-width="formLabelWidth">
              <el-input v-model="form.answer" autocomplete="off"></el-input>
            </el-form-item>
          </el-form>
          <div slot="footer" class="dialog-footer">
            <el-button @click="dialogFormVisible = false">取 消</el-button>
            <el-button type="primary" @click="onAddNewQuestion"
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
        title: '',
        question: '',
        optionA: '',
        optionB: '',
        optionC: '',
        optionD: '',
        answer: ''
      },
      formInline: {
        user: '',
        region: ''
      },
      tableData: [
        {
          id: 1,
          question: '法国的首都是什么?',
          options: '巴黎,伦敦,纽约,东京',
          answer: '巴黎'
        },
        {
          id: 2,
          question: '中国的首都是哪里?',
          options: '上海,北京,广州,深圳',
          answer: '北京'
        },
        {
          id: 3,
          question: '1 + 1 等于几?',
          options: '1,2,3,4',
          answer: '2'
        },
        {
          id: 4,
          question: '下列哪个是编程语言?',
          options: '土豆,Java,苹果,白菜',
          answer: 'Java'
        },
        {
          id: 5,
          question: '地球围绕什么转?',
          options: '月亮,火星,太阳,金星',
          answer: '太阳'
        }
      ]
    }
  },
  methods: {
    onSubmit() {
      console.log('submit!')
    },
    onAddNewQuestion() {
      console.log('add new question!')
      this.dialogFormVisible = false
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
