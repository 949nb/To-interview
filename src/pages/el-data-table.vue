<template>
  <div>
    <div>
      <el-form-renderer inline :content="content" ref="form">
        <el-form-item>
          <el-button type="primary" @click="printValue">搜索</el-button>
          <el-button @click="data = {}">重置</el-button>
        </el-form-item>
      </el-form-renderer>
      <pre>{{ data }}</pre>
    </div>
    <el-data-table v-bind="$data" />
  </div>
</template>

<script>
// 全局引入el-data-table
import Vue from 'vue'

// register component and loading directive
import ElDataTable from '@femessage/el-data-table'
import ElFormRenderer from '@femessage/el-form-renderer'
import Axios from '../plugins/axios'

Vue.component('el-form-renderer', ElFormRenderer)
Vue.component('el-data-table', ElDataTable)

// if the table component cannot access `this.$axios`, it cannot send request

export default {
  name: 'on-new-edit-delete',
  data() {
    return {
      url: '',
      columns: [
        {prop: 'name', label: '用户名'},
        {prop: 'createdBy', label: '创建人'},
        {prop: 'userInfo.createTime', label: '创建时间'}
      ],
      searchForm: [],
      data: {},
      content: [
        // el-data-renderer生成需要的配置
        {
          id: 'itemName',
          type: 'input',
          label: '组件名称',
          el: {
            placeholder: '请输入'
          }
        },
        {
          id: 'a',
          type: 'input',
          label: '分类',
          default: 'alvin',
          el: {
            placeholder: '请选择'
          }
        },
        {
          id: 'formStatus',
          type: 'select',
          label: '状态',
          el: {
            placeholder: '请选择'
          },
          options: [
            {
              label: 'shanghai',
              value: 'shanghai'
            },
            {
              label: 'beijing',
              value: 'beijing'
            }
          ]
        }
      ]
    }
  },
  methods: {
    printValue() {
      this.data = this.$refs.form.getFormValue()
    }
  }
}
</script>
