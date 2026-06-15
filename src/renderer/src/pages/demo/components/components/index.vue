<template>
  <div class="components view-component-container">
    <t-card title="按钮组件" header-bordered>
      <t-space>
        <t-button theme="primary">主要按钮</t-button>
        <t-button theme="default">默认按钮</t-button>
        <t-button theme="danger">危险按钮</t-button>
        <t-button theme="warning">警告按钮</t-button>
        <t-button theme="success">成功按钮</t-button>
      </t-space>
    </t-card>

    <t-card title="标签页" header-bordered class="mt-4">
      <t-tabs v-model="tabValue">
        <t-tab-panel value="first" label="选项一">
          <p>选项一内容</p>
        </t-tab-panel>
        <t-tab-panel value="second" label="选项二">
          <p>选项二内容</p>
        </t-tab-panel>
        <t-tab-panel value="third" label="选项三">
          <p>选项三内容</p>
        </t-tab-panel>
      </t-tabs>
    </t-card>

    <t-card title="进度条" header-bordered class="mt-4">
      <t-space direction="vertical">
        <t-progress :percentage="30" />
        <t-progress :percentage="60" color="var(--td-warning-color)" />
        <t-progress :percentage="100" color="var(--td-success-color)" />
      </t-space>
    </t-card>
  </div>
</template>
<script setup lang="ts">
import { ref } from 'vue';

defineOptions({
  name: 'DemoComponents',
});

const tabValue = ref('first');
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
