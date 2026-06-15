<template>
  <div class="charts view-component-container">
    <t-card title="简单图表展示" header-bordered>
      <p>图表区域（可集成 ECharts 等图表库）</p>
      <div class="chart-placeholder">
        <t-alert theme="info" message="此处可放置图表组件" />
      </div>
    </t-card>

    <t-card title="数据分布" header-bordered class="mt-4">
      <t-table :data="tableData" :columns="columns" />
    </t-card>
  </div>
</template>
<script setup lang="ts">
import { ref } from 'vue';

defineOptions({
  name: 'DemoCharts',
});

const columns = [
  { colKey: 'name', title: '名称' },
  { colKey: 'value', title: '数值' },
  { colKey: 'type', title: '类型' },
];

const tableData = ref([
  { name: '数据 A', value: 120, type: '类型 1' },
  { name: '数据 B', value: 85, type: '类型 2' },
  { name: '数据 C', value: 200, type: '类型 1' },
  { name: '数据 D', value: 150, type: '类型 3' },
]);
</script>
<style lang="less" scoped>
.view-component-container {
  padding: var(--td-size-4);
  height: 100%;
  overflow-y: auto;
}

.mt-4 {
  margin-top: var(--td-size-4);
}

.chart-placeholder {
  height: 200px;
  display: flex;
  align-items: center;
  justify-content: center;
  background-color: var(--td-bg-color-secondarycontainer);
  border-radius: var(--td-radius-default);
}
</style>
