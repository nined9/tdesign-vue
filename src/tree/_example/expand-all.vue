<template>
  <t-space direction="vertical">
    <t-space>
      <span>切换数据:</span>
      <t-switch @change="toggleData" />
    </t-space>
    <t-space>
      <span>展开动画:</span>
      <t-switch v-model="transition" />
    </t-space>
    <t-tree :data="items" :label="label" expand-all :transition="transition" />
  </t-space>
</template>

<script>
const data1 = [
  {
    value: 't1',
    children: [
      {
        value: 't1.1',
        children: [
          {
            value: 't1.1.1',
          },
          {
            value: 't1.1.2',
          },
        ],
      },
      {
        value: 't1.2',
        children: [
          {
            value: '1.2.1',
          },
          {
            value: '1.2.2',
          },
        ],
      },
    ],
  },
  {
    value: 't2',
    children: [
      {
        value: 't2.1',
      },
      {
        value: 't2.2',
      },
    ],
  },
];

const data2 = [
  {
    value: 'd1',
    children: [
      {
        value: 'd1.1',
        label: 'd1.1 custom label',
        children: [
          {
            value: 'd1.1.1',
          },
        ],
      },
      {
        value: 'd1.2',
        children: [
          {
            value: 'd1.2.1',
          },
          {
            value: 'd1.2.2',
          },
        ],
      },
    ],
  },
  {
    value: 'd2',
    children: [
      {
        value: 'd2.1',
      },
      {
        value: 'd2.2',
      },
    ],
  },
];

export default {
  data() {
    return {
      transition: true,
      items: data1,
    };
  },
  methods: {
    toggleData() {
      const items = this.items[0].value === 't1' ? data2 : data1;
      this.items = items;
    },
    label(createElement, node) {
      return node.label || node.value;
    },
  },
};
</script>
