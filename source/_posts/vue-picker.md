---
title: 基于vue.js的选择器组件
date: 2016-10-23 19:27:58
tags:
---


# 概述

基于vue.js选择器组件

# DEMO

![code.png][1]

# 安装

```Bash
npm install vue-3d-picker --save
```

```JavaScript
import picker from 'vue-3d-picker';
Vue.component(picker.name, picker);
```

# 基础用法
```HTML
<picker v-model="visible" :data-items="items" @change="onValuesChange">
	<div class="top-content" slot="top-content">Top of the content.</div>
	<div class="bottom-content" slot="bottom-content">Bottom of the content.</div>
</picker>
```

```JavaScript
export default {
  methods: {
    onValuesChange(result, pickerEl, reset) {
      let year = result[0], month = result[1];
      // result -> 结果
      // pickerEl -> 方法
      // reset -> 重置  usage: reset(index, newData)
    }
  },

  data() {
    return {
      visible: true,
      items: [
        {
          values: ['2000', '2001', '2002', '2003', '2004', '2005', '2006', '2007'],
        }, {
          values: ['1', '2', '3', '4', '5', '6', '7', '8', '9', '10', '11', '12'],
        }
      ]
    }
  }
}
```

# 选项

Picker Options:

| 参数 | 描述 |
| ----- | ----- |
| v-model | 默认值为false，控制显示和隐藏 |
| :data-items | 默认值为[]，显示的数组|
| @change | 内容改变时执行的监听函数 |


Picker Items Options:

| 参数 | 描述 | 类型 | 默认值 |
| ----- | ----- | ----- | ----- |
| index | 默认选中的索引值 | Number | 0 |
| values | 赋值的数组 | Array | [] |
| width | 显示的宽度，单位是 % | String | 'flex' |
| name | 显示数据的字段名，默认值是value .| String | 'value' |
 
# 例子

```Bash
npm init
npm run dev
```

# 注意

需要 [postcss-loader][2] 来支持picker组件的兼容性.


  [1]: https://xiecg.github.io/other/vue-picker/code.png
  [2]: https://github.com/postcss/postcss-loader