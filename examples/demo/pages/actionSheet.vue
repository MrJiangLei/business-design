<template>
  <div>
    <demo-block title="基本用法">
      <wd-button type="primary" @click="show1 = true">弹出菜单</wd-button>
      <wd-action-sheet v-model="show1" :actions="actions1" />
    </demo-block>
    <demo-block title="选项状态">
      <wd-button type="primary" @click="show2 = true">弹出菜单</wd-button>
      <wd-action-sheet v-model="show2" :actions="actions2" />
    </demo-block>
    <demo-block title="取消按钮">
      <wd-button type="primary" @click="show3 = true">弹出菜单</wd-button>
      <wd-action-sheet v-model="show3" :actions="actions1" cancel-text="取消" />
    </demo-block>
    <demo-block title="标题">
      <wd-button type="primary" @click="show4 = true">弹出菜单</wd-button>
      <wd-action-sheet v-model="show4" title="标题">
        <p style="padding: 15px 15px 150px 15px;">内容</p>
      </wd-action-sheet>
    </demo-block>
  </div>
</template>

<script>
export default {
  data () {
    return {
      show1: false,
      actions1: [
        {
          name: '选项1'
        }, {
          name: '选项2'
        }, {
          name: '选项3',
          subname: '描述信息'
        }
      ],
      show2: false,
      actions2: [
        {
          name: '颜色',
          color: '#0083ff'
        }, {
          name: '禁用',
          disabled: true
        }, {
          loading: true
        }
      ],
      show3: false,
      show4: false
    }
  }
}
</script>
