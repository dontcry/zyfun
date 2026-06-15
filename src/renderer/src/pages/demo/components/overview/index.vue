<template>
  <div class="overview view-component-container">
    <t-card title="欢迎使用演示页面" header-bordered>
      <p>这是一个演示页面，用于展示各种 UI 组件和功能。</p>
    </t-card>

    <t-card title="统计卡片" header-bordered class="mt-4">
      <t-row :gutter="16">
        <t-col :span="3">
          <t-statistic title="用户数" :value="12580" trend="increase" />
        </t-col>
        <t-col :span="3">
          <t-statistic title="访问量" :value="89340" trend="increase" />
        </t-col>
        <t-col :span="3">
          <t-statistic title="订单数" :value="3420" trend="decrease" />
        </t-col>
        <t-col :span="3">
          <t-statistic title="转化率" :value="3.6" suffix="%" trend="increase" />
        </t-col>
      </t-row>
    </t-card>

    <t-card title="最近动态" header-bordered class="mt-4">
      <t-timeline>
        <t-timeline-item label="2024-06-01">项目初始化</t-timeline-item>
        <t-timeline-item label="2024-06-05">完成基础架构</t-timeline-item>
        <t-timeline-item label="2024-06-10">添加演示页面</t-timeline-item>
      </t-timeline>
    </t-card>
  </div>
</template>
<script setup lang="ts">
defineOptions({
  name: 'DemoOverview',
});
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
</style>
