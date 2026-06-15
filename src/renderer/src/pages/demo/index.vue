<template>
  <div class="demo view-container">
    <common-nav :list="componentNav" :active="active.nav" class="sidebar" @change="onNavChange" />

    <div class="content">
      <div class="container">
        <keep-alive>
          <component :is="currentComponent" class="content-wrapper"></component>
        </keep-alive>
      </div>
    </div>
  </div>
</template>
<script setup lang="ts">
import { computed, defineAsyncComponent, ref, shallowRef } from 'vue';

import CommonNav from '@/components/common-nav/index.vue';

const componentMap = {
  overview: defineAsyncComponent(() => import('./components/overview/index.vue')),
  components: defineAsyncComponent(() => import('./components/components/index.vue')),
  charts: defineAsyncComponent(() => import('./components/charts/index.vue')),
  forms: defineAsyncComponent(() => import('./components/forms/index.vue')),
};

const componentNav = computed(() => [
  { id: 'overview', name: '概览' },
  { id: 'components', name: '组件' },
  { id: 'charts', name: '图表' },
  { id: 'forms', name: '表单' },
]);

const active = ref({
  nav: 'overview',
});

const currentComponent = shallowRef(componentMap[Object.keys(componentMap)[0]]);

const onNavChange = (item: string) => {
  active.value.nav = item;

  if (Object.hasOwn(componentMap, item)) {
    currentComponent.value = componentMap[item];
  }
};
</script>
<style lang="less" scoped>
.view-container {
  height: 100%;
  width: 100%;
  display: flex;
  flex-direction: row;
  gap: var(--td-size-4);

  .sidebar {
    flex-grow: 0;
    flex-shrink: 0;
  }

  .content {
    height: 100%;
    width: 100%;
    flex: 1;
    display: flex;
    flex-direction: column;
    gap: var(--td-size-4);
    overflow: hidden;

    .container {
      flex: 1;
      height: 100%;
      width: 100%;

      .content-wrapper {
        width: 100%;
        height: 100%;
        position: relative;
      }
    }
  }
}
</style>
