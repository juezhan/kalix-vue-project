<!--
描述：艺术中心-招聘管理-公司招聘
开发人：hqj-修改
开发日期：2017年12月18日
-->

<template lang="pug">
  keep-alive
    base-table(bizKey="artRecruit" title='招聘信息列表' v-bind:targetURL="targetURL"
    v-bind:bizDialog="bizDialog" v-bind:tableFields="tableFields" bizSearch="ArtRecruitSearch" v-bind:btnList="btnList"
    v-bind:dictDefine="dictDefine" v-bind:isFixedColumn="isFixedColumn")
</template>

<script type="text/ecmascript-6">
  import BaseTable from '@/components/custom/baseTable'
  import {RecruitURL, RecruitComponent, ToolButtonList} from '../config.toml'
  import {registerComponent} from '@/api/register'

  // 注册全局组件
  registerComponent(RecruitComponent)

  export default {
    data() {
      return {
        dictDefine: [{ // 定义数据字典的显示
          cacheKey: 'ART-DICT-KEY',
          type: '企业性质',
          targetField: 'companyNatureName',
          sourceField: 'companyNature'
        }, {
          cacheKey: 'ART-DICT-KEY',
          type: '省份',
          targetField: 'regionName',
          sourceField: 'region'
        }, {
          cacheKey: 'ART-DICT-KEY',
          type: '工作类型',
          targetField: 'jobTypeName',
          sourceField: 'jobType'
        }, {
          cacheKey: 'ART-DICT-KEY',
          type: '月薪',
          targetField: 'probationSalaryName',
          sourceField: 'probationSalary'
        }, {
          cacheKey: 'ART-DICT-KEY',
          type: '月薪',
          targetField: 'salaryName',
          sourceField: 'salary'
        }],
        btnList: ToolButtonList,
        targetURL: RecruitURL,
        tableFields: [
          {prop: 'companyName', label: '企业名称'},
          {prop: 'companyNatureName', label: '企业性质'},
          {prop: 'companyEmail', label: '企业邮箱'},
          {prop: 'companyPhone', label: '企业固定电话'},
          {prop: 'publishDate', label: '发布时间', width: '160'},
          {prop: 'regionName', label: '工作省份'},
          {prop: 'city', label: '工作城市'},
          {prop: 'position', label: '岗位名称'},
          {prop: 'probationSalaryName', label: '实习薪资'},
          {prop: 'salaryName', label: '转正薪资'},
          {prop: 'jobTypeName', label: '工作类型'}
        ],
        bizDialog: [
          {id: 'view', dialog: 'ArtRecruitView'},
          {id: 'edit', dialog: 'ArtRecruitEdit'},
          {id: 'add', dialog: 'ArtRecruitAdd'}
        ],
        isFixedColumn: true
      }
    },
    created() {
    },
    methods: {},
    components: {
      BaseTable
    }
  }
</script>

<style scoped lang="stylus">

</style>
