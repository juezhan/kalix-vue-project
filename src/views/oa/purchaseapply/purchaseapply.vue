<!--
描述：办公自动化-采购申请
开发人：hqj
开发日期：2017年10月31日
-->
<template lang="pug">
  div
    keep-alive
      base-table(bizKey='purchaseApply' title='采购申请列表' v-bind:targetURL='targetURL'
      v-bind:bizDialog='bizDialog' bizSearch='OaPurchaseApplySearch' v-bind:btnList='btnList'
      v-bind:isFixedColumn="isFixedColumn" v-bind:customTableTool="customTableTool")
        template(slot="tableColumnSlot")
          kalix-biz-no-column // 业务编号
          el-table-column(prop="title" label="名称" align="center" width="220")
          kalix-date-column(prop="creationDate" label="创建时间")
          el-table-column(prop="orgName" label="申请部门" align="center" width="220")
          kalix-date-column(prop="applyDate" label="申请时间")
          el-table-column(prop="reason" label="用车事由" align="center" width="220")
          el-table-column(prop="usageCount" label="乘车人数" align="center" width="220")
          el-table-column(prop="address" label="用车起始地点" align="center" width="220")
          el-table-column(prop="cityName" label="市内用车" align="center" width="220")
          el-table-column(prop="createBy" label="经办人" align="center" width="90")
          el-table-column(prop="auditResult" label="审批结果" align="center" width="220")
          el-table-column(prop="currentNode" label="当前环节" align="center" width="220")
          kalix-process-status-column
    kalix-task-view(ref="kalixDialog")
</template>

<script type="text/ecmascript-6">
  import BaseTable from '@/components/custom/baseTable'
  import {PurchaseApplyURL, PurchaseApplyComponent, PurchaseApplyStartURL} from '../config.toml'
  import {registerComponent} from '@/api/register'
  import {workflowBtnList, registerComp, customTableTool} from '@/views/oa/comp'
  import BizNoColumn from '@/views/oa/comp/bizNoColumn'
  import DateColumn from 'views/oa/comp/dateColumn'
  import ProcessStatusColumn from '@/views/oa/comp/processStatusColumn.vue'
  import TaskView from '@/views/oa/comp/taskView'

  // 注册全局组件
  registerComponent(PurchaseApplyComponent)

  export default {
    data() {
      return {
        isFixedColumn: true,
        hasTableSelection: true,
        btnList: workflowBtnList,
        targetURL: PurchaseApplyURL,
        bizDialog: [
          {id: 'view', dialog: 'OaPurchaseApplyView'},
          {id: 'edit', dialog: 'OaPurchaseApplyAdd'},
          {id: 'add', dialog: 'OaPurchaseApplyAdd'},
          {id: 'progress', dialog: 'OaTaskView'}
        ]
      }
    },
    components: {
      BaseTable,
      KalixBizNoColumn: BizNoColumn,
      KalixDateColumn: DateColumn,
      KalixProcessStatusColumn: ProcessStatusColumn, // 工作流状态列
      KalixTaskView: TaskView
    },
    created() {
    },
    mounted() {
      registerComp()
    },
    methods: {
      customTableTool(row, btnId) {
        customTableTool(row, btnId, PurchaseApplyStartURL, this)
      }
    }
  }
</script>

<style scoped lang="stylus">

</style>
