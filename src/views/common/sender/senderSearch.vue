<!--
描述：我的首页-发件箱组件-查詢组件
开发人：桑杨
开发日期：2017年8月29日
-->

<template lang="pug">
  kalix-search(title="发件查询"
  v-bind:bizKey="bizKey" v-bind:searchForm="formModel"
  v-bind:form-rules="rules")
    div(slot="searchFormSlot")
      el-form-item(label="收件人" prop="receiverNames")
        el-input(v-model.trim="formModel.receiverNames" placeholder="请输入类型名" auto-complete="off"
        v-bind:class="bindCls('receiverNames')" field="receiverNames" data-type="string")
      el-form-item(label="消息主题" prop="title")
        el-input(v-model.trim="formModel.title" placeholder="请输入类型名" auto-complete="off"
        v-bind:class="bindCls('title')" field="title"  data-type="string")
      el-form-item(label="发件时间" prop="beginDate_begin")
        el-date-picker(v-model="formModel.beginDate_begin" v-on:change="beginChange" placeholder="选择日期"
        type="date" data-type="datetime" v-bind:class="bindCls('beginDate_begin')" field="creationDate:begin:gt")
      el-form-item(label="-" prop="beginDate_end")
        el-date-picker(v-model="formModel.beginDate_end" v-on:change="endChange" placeholder="选择日期"
        type="date" data-type="datetime" v-bind:class="bindCls('beginDate_end')" field="creationDate:end:lt" )
</template>

<script type="text/ecmascript-6">
  import BaseSearch from '@/components/custom/baseSearch.vue'
  import {SearchDataMixin} from '@/common/searchmixin'

  export default {
    mixins: [SearchDataMixin],
    data() {
      return {
        bizKey: 'receiver',
        formModel: {
          receiverNames: '',
          title: '',
          beginDate_begin: '',
          beginDate_end: ''
        },
        rules: {
          receiverNames: [],
          title: [],
          beginDate_begin: [],
          beginDate_end: []
        }
      }
    },
    created() {
    },
    components: {
      KalixSearch: BaseSearch
    },
    methods: {}
  }
</script>

<style scoped lang="stylus" type="text/stylus">
</style>
