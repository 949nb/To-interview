<template>
  <div>
    <div id="el-data-table">
      <!-- ·搜索表单· -->
      <el-row class="search-form" :gutter="20">
        <el-form :model="searchForm" @submit.native.prevent label-width="40px">
          <!-- 搜索表单 · 组件名称 -->
          <el-col :span="4">
            <el-form-item label="组件名称" label-width="80px">
              <el-input v-model="searchForm.formName"></el-input>
            </el-form-item>
          </el-col>
          <!-- 搜索表单 · 分类 -->
          <el-col :span="4">
            <el-form-item label="分类">
              <el-select
                v-model="searchForm.classification"
                placeholder="请选择"
              >
                <el-option
                  v-for="item in classificationOption"
                  :key="item.value"
                  :label="item.label"
                  :value="item.value"
                ></el-option>
              </el-select>
            </el-form-item>
          </el-col>
          <!-- 搜索表单 · 状态 -->
          <el-col :span="4">
            <el-form-item label="状态">
              <el-select v-model="searchForm.formStatus" placeholder="请选择">
                <el-option
                  v-for="item in formStatusOption"
                  :key="item.value"
                  :label="item.label"
                  :value="item.value"
                ></el-option>
              </el-select>
            </el-form-item>
          </el-col>
          <!-- 搜索表单 · 按钮 -->
          <el-col :span="4">
            <el-button type="primary" @click="search">查询</el-button>
            <el-button @click="resetSearch">重置</el-button>
          </el-col>
        </el-form>
      </el-row>
      <!-- 展示表格 -->
      <div class="showTable">
        <div class="topBtn">
          <el-button type="primary" @click="add">新增</el-button>
          <el-button type="danger" @click="danger">删除</el-button>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      searchForm: {
        formName: '',
        classification: '',
        formStatus: ''
      },
      classificationOption: [
        {
          value: '0',
          label: '选项一'
        },
        {
          value: '1',
          label: '选项二'
        }
      ],
      formStatusOption: [
        {
          value: '0',
          label: '完成'
        },
        {
          value: '1',
          label: '未完成'
        },
        {
          value: '2',
          label: '正在完成中'
        }
      ]
    }
  },
  methods: {
    search() {
      console.log(this.searchForm)
    },
    resetSearch() {
      for (let key in this.searchForm) {
        this.searchForm[key] = ''
      }
    }
  }
}
</script>

<style lang="less"></style>
