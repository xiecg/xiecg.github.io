---
title: 基于vue.js的图像预览组件
date: 2016-12-08 21:01:33
tags:
---

[postcss-salad]: https://github.com/ElemeFE/postcss-salad
[vue-fancybox]: https://xiecg.github.io/other/vue-fancybox/#/baseUsage
[github]: https://github.com/xiecg/vue-fancybox

## Overview
基于vue.js图像预览组件 

> 更多的手势操作还是开发中

## Demo

[vue-fancybox]

## Github

[github]

## 安装
```Bash
npm install vue-fancybox --save
```

```JavaScript
import fancyBox from 'vue-fancybox';
```

## 基础用法
```HTML
<div class="list" v-for="(n, index) in imageList" :data-index="index">
  <img @click="open($event)" :src="n.url">
</div>
```

```JavaScript
export default {
  data () {
    return {
      imageList: [
        { width: 900, height: 675, url: 'http://ocm0knkb1.bkt.clouddn.com/1-1.jpg' },
        { width: 601, height: 1024, url: 'http://ocm0knkb1.bkt.clouddn.com/1-2.jpg' },
        { width: 1024, height: 700, url: 'http://ocm0knkb1.bkt.clouddn.com/1-3.jpg' }
      ]
    }
  },
  methods: {
    open (e) {
      fancyBox(e.target, this.imageList);
    }
  }
}
```

## 选项

fancyBox Parameter:

| Parameter | Description |
| ----- | ----- |
| e.target | 当前点击的图片 |
| this.imageList | 所有的图片列表 |

this.imageList Options:

| Option | Description | Type |
| ----- | ----- | ----- |
| width | 图片的宽度 | Number |
| height | 图片的高度 | Number |
| url | 图片的的地址 | String |

## 例子

```Bash
$ cd example
$ npm install
$ npm run dev
```

## 注意

需要 [postcss-salad] 配合
