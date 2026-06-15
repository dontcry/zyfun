<template>
  <div class="forms view-component-container">
    <t-card title="基础表单" header-bordered>
      <t-form :data="formData" :rules="rules" @submit="onSubmit">
        <t-form-item label="用户名" name="username">
          <t-input v-model="formData.username" placeholder="请输入用户名" />
        </t-form-item>
        <t-form-item label="邮箱" name="email">
          <t-input v-model="formData.email" placeholder="请输入邮箱" />
        </t-form-item>
        <t-form-item label="性别" name="gender">
          <t-radio-group v-model="formData.gender">
            <t-radio value="male">男</t-radio>
            <t-radio value="female">女</t-radio>
          </t-radio-group>
        </t-form-item>
        <t-form-item label="兴趣爱好" name="hobbies">
          <t-checkbox-group v-model="formData.hobbies">
            <t-checkbox value="reading">阅读</t-checkbox>
            <t-checkbox value="sports">运动</t-checkbox>
            <t-checkbox value="music">音乐</t-checkbox>
          </t-checkbox-group>
        </t-form-item>
        <t-form-item>
          <t-button theme="primary" type="submit">提交</t-button>
          <t-button theme="default" @click="onReset">重置</t-button>
        </t-form-item>
      </t-form>
    </t-card>
  </div>
</template>
<script setup lang="ts">
import { MessagePlugin } from 'tdesign-vue-next';
import { reactive } from 'vue';

defineOptions({
  name: 'DemoForms',
});

const formData = reactive({
  username: '',
  email: '',
  gender: 'male',
  hobbies: [],
});

const rules = {
  username: [{ required: true, message: '用户名必填', type: 'error' }],
  email: [{ required: true, message: '邮箱必填', type: 'error' }],
};

const onSubmit = ({ validateResult }: { validateResult: boolean }) => {
  if (validateResult) {
    MessagePlugin.success('提交成功');
  } else {
    MessagePlugin.error('表单校验失败');
  }
};

const onReset = () => {
  formData.username = '';
  formData.email = '';
  formData.gender = 'male';
  formData.hobbies = [];
};
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
