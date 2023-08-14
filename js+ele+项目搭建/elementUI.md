---

title: ElementUI学习笔记
date: 2023-7-23
tags:
 - ElementUI 
categories:
 - ElementUI
---
<h1><center>ElementUI</center></h1>

[TOC]

# 一、介绍ElementUI

ElementUI中文网 ：https://element.eleme.cn/#/zh-CN

Element-Ul是饿了么前端团队推出的一款基于Vue.js 2.0 的桌面端UI框架，手机端有对应框架是Mint UI 。

## 1.1、设计原则

### 1.1.1、一致 Consistency

- 与现实生活一致：与现实生活的流程、逻辑保持一致，遵循用户习惯的语言和概念；

- 在界面中一致：所有的元素和结构需保持一致，比如：设计样式、图标和文本、元素的位置等。

###  1.1.2、反馈 Feedback

- 控制反馈：通过界面样式和交互动效让用户可以清晰的感知自己的操作；

- 页面反馈：操作后，通过页面元素的变化清晰地展现当前状态。

### 1.1.3、效率 Efficiency

- 简化流程：设计简洁直观的操作流程；

- 清晰明确：语言表达清晰且表意明确，让用户快速理解进而作出决策；

- 帮助用户识别：界面简单直白，让用户快速识别而非回忆，减少用户记忆负担。

### 1.1.4、可控 Controllability

- 用户决策：根据场景可给予用户操作建议或安全提示，但不能代替用户进行决策；

- 结果可控：用户可以自由的进行操作，包括撤销、回退和终止当前操作等。

# 二、入门

## 2.1、安装：

### 2.1.1、方法一：

目前可以通过 unpkg.com/element-ui 获取到最新版本的资源，在页面上引入 js 和 css 文件即可开始使用。
```html
<!-- 引入样式 -->
<link rel="stylesheet" href="https://unpkg.com/element-ui/lib/theme-chalk/index.css">
<!-- 引入组件库 -->
<script src="https://unpkg.com/element-ui/lib/index.js"></script>
```
### 2.1.2、方法二：

```bash
npm install element-ui -S
```

main.js文件引入

```js
import ElementUI from 'element-ui'
import 'element-ui/lib/theme-chalk/index.css'
Vue.use(ElementUI)
```

# 三.组件

## 3.1、基本组件

### 3.1.1、Layout 布局

通过基础的 24 分栏，迅速简便地创建布局。通过 row 和 col 组件，并通过 col 组件的 span 属性就可以自由地组合布局。
```html
<el-row>
  <el-col :span="24"><div class="grid-content bg-purple-dark"></div></el-col>
</el-row>
<el-row>
  <el-col :span="12"><div></div></el-col>
  <el-col :span="12"><div></div></el-col>
</el-row>    
```

分栏间隔

分栏之间存在间隔。Row 组件 提供 gutter 属性来指定每一栏之间的间隔，默认间隔为 0。
```html
<el-row :gutter="20">
  <el-col :span="6"><div></div></el-col>
  <el-col :span="6"><div></div></el-col>
  <el-col :span="6"><div></div></el-col>
  <el-col :span="6"><div></div></el-col>
</el-row>
```

分栏偏移

支持偏移指定的栏数。通过制定 col 组件的 offset 属性可以指定分栏偏移的栏数。
```html
<el-row :gutter="20">
  <el-col :span="6"><div></div></el-col>
  <el-col :span="6" :offset="6"><div></div></el-col>
</el-row>
<el-row :gutter="20">
  <el-col :span="6" :offset="6"><div></div></el-col>
  <el-col :span="6" :offset="6"><div></div></el-col>
</el-row>
<el-row :gutter="20">
  <el-col :span="12" :offset="6"><div></div></el-col>
</el-row>
```

对齐方式

通过 flex 布局来对分栏进行灵活的对齐。

将 type 属性赋值为 'flex'，可以启用 flex 布局，并可通过 justify 属性来指定 start, center, end, space-between, space-around 其中的值来定义子元素的排版方式。
```html
<el-row type="flex" class="row-bg">
  <el-col :span="6"><div></div></el-col>
  <el-col :span="6"><div></div></el-col>
  <el-col :span="6"><div></div></el-col>
</el-row>
```

响应式布局

参照了 Bootstrap 的 响应式设计，预设了五个响应尺寸：xs、sm、md、lg 和 xl。
```html
<el-row :gutter="10">
  <el-col :xs="8" :sm="6" :md="4" :lg="3" :xl="1"><div></div></el-col>
  <el-col :xs="4" :sm="6" :md="8" :lg="9" :xl="11"><div></div></el-col>
  <el-col :xs="4" :sm="6" :md="8" :lg="9" :xl="11"><div></div></el-col>
  <el-col :xs="8" :sm="6" :md="4" :lg="3" :xl="1"><div></div></el-col>
</el-row>
    基于断点的隐藏类 相关参数说明
    hidden-xs-only - 当视口在 xs 尺寸时隐藏
    hidden-sm-only - 当视口在 sm 尺寸时隐藏
    hidden-sm-and-down - 当视口在 sm 及以下尺寸时隐藏
    hidden-sm-and-up - 当视口在 sm 及以上尺寸时隐藏
    hidden-md-only - 当视口在 md 尺寸时隐藏
    hidden-md-and-down - 当视口在 md 及以下尺寸时隐藏
    hidden-md-and-up - 当视口在 md 及以上尺寸时隐藏
    hidden-lg-only - 当视口在 lg 尺寸时隐藏
    hidden-lg-and-down - 当视口在 lg 及以下尺寸时隐藏
    hidden-lg-and-up - 当视口在 lg 及以上尺寸时隐藏
    hidden-xl-only - 当视口在 xl 尺寸时隐藏
```

### 3.1.2、Container 布局容器

用于布局的容器组件，方便快速搭建页面的基本结构：

  \<el-container>：外层容器。当子元素中包含 \<el-header> 或 \<el-footer> 时，全部子元素会垂直上下排列，否则会水平左右排列。
  \<el-header>：顶栏容器。
  \<el-aside>：侧边栏容器。
  \<el-main>：主要区域容器。
  \<el-footer>：底栏容器。

以上组件采用了 flex 布局，使用前请确定目标浏览器是否兼容。此外，\<el-container> 的子元素只能是后四者，后四者的父元素也只能是 \<el-container>。

常见页面布局
```html
<body>
<div id="app">
  <el-header></el-header>
  <el-container>
      <el-header>Header</el-header>
      <el-main>Main</el-main>
      <el-footer>footer</el-footer>
  </el-container>
</div>
</body>
```

### 3.1.3、Color 色彩

Element 为了避免视觉传达差异，使用一套特定的调色板来规定颜色，为你所搭建的产品提供一致的外观视觉感受。
主色    Element 主要品牌颜色是鲜艳、友好的蓝色。
辅助色  除了主色外的场景色，需要在不同的场景中使用（例如危险色表示危险的操作）。
中性色  中性色用于文本、背景和边框颜色。通过运用不同的中性色，来表现层次结构。

### 3.1.4、Typography 字体


### 3.1.5、Border 边框

### 3.1.6、Icon 图标

提供了一套常用的图标集合。

```html
<i class="el-icon-edit"></i>
<i class="el-icon-share"></i>
<i class="el-icon-delete"></i>
<i class="el-icon-light-rain"></i>

<i class="el-icon-date"></i>
<i class="el-icon-loading"></i>
<i class="el-icon-view"></i>
<i class="el-icon-folder-add"></i>
```

### 3.1.7、Button 按钮

常用的操作按钮。
使用type、plain、round和circle属性来定义 Button 的样式。
```html
<el-button>默认按钮</el-button>
<el-button type="primary">主要按钮</el-button>
<el-button type="success">成功按钮</el-button>
<el-button type="info">信息按钮</el-button>
<el-button type="warning">警告按钮</el-button>
<el-button type="danger">危险按钮</el-button>
<el-button plain>朴素按钮</el-button>
<el-button type="primary" plain>主要按钮</el-button>
<el-button type="success" plain>成功按钮</el-button>
<el-button type="info" plain>信息按钮</el-button>
<el-button type="warning" plain>警告按钮</el-button>
<el-button type="danger" plain>危险按钮</el-button>

<el-button round>圆角按钮</el-button>
<el-button type="primary" round>主要按钮</el-button>
<el-button type="success" round>成功按钮</el-button>
<el-button type="info" round>信息按钮</el-button>
<el-button type="warning" round>警告按钮</el-button>
<el-button type="danger" round>危险按钮</el-button>

<el-button icon="el-icon-search" circle></el-button>
<el-button type="primary" icon="el-icon-edit" circle></el-button>
<el-button type="success" icon="el-icon-check" circle></el-button>
<el-button type="info" icon="el-icon-message" circle></el-button>
<el-button type="warning" icon="el-icon-star-off" circle></el-button>
<el-button type="danger" icon="el-icon-delete" circle></el-button>
```

### 3.1.8、Link 文字链接

```html
<el-link href="https://element.eleme.io" target="_blank">默认链接</el-link>
<el-link type="primary">主要链接</el-link>
<el-link type="success">成功链接</el-link>
<el-link type="warning">警告链接</el-link>
<el-link type="danger">危险链接</el-link>
<el-link type="info">信息链接</el-link>
```



## 3.2、表单组件

### 3.2.1、Radio 单选框

在一组备选项中进行单选

由于选项默认可见，不宜过多，若选项过多，建议使用 Select 选择器。

```html
   <el-radio v-model="radio" label="1">备选项</el-radio>
   <el-radio v-model="radio" label="2">备选项</el-radio>
```
### 3.2.2、Checkbox 多选框

一组备选项中进行多选


单独使用可以表示两种状态之间的切换，写在标签中的内容为 checkbox 按钮后的介绍。
checkbox-group元素能把多个 checkbox 管理为一组，只需要在 Group 中使用v-model绑定Array类型的变量即可。 el-checkbox 的 label属性是该 checkbox 对应的值，若该标签中无内容，则该属性也充当 checkbox 按钮后的介绍。label与数组中的元素值相对应，如果存在指定的值则为选中状态，否则为不选中。

```html
<el-checkbox-group v-model="checkList">
    <el-checkbox label="复选框 A"></el-checkbox>
    <el-checkbox label="复选框 B"></el-checkbox>
    <el-checkbox label="复选框 C"></el-checkbox>
    <el-checkbox label="禁用" disabled></el-checkbox>
    <el-checkbox label="选中且禁用" disabled></el-checkbox>
</el-checkbox-group>
      
```
### 3.2.3、Input输入框

使用clearable属性即可得到一个可清空的输入框

使用show-password属性即可得到一个可切换显示隐藏的密码框

可以通过 prefix-icon 和 suffix-icon 属性在 input 组件首部和尾部增加显示图标，也可以通过 slot 来放置图标。

```html

<el-input class="el-input" placeholder="请输入内容" v-model="input" clearable></el-input>
<label>密码</label>
<el-input class="el-input" placeholder="请输入密码" v-model="input2" show-password></el-input>   
<el-input placeholder="请输入内容" prefix-icon="el-icon-search" v-model="input3"></el-input>
```

### 3.2.4、InputNumber 计数器

仅允许输入标准的数字值，可定义范围

### 3.2.5、Select 选择器

当选项过多时，使用下拉菜单展示并选择内容。


(6).Cascader 级联选择器

当一个数据集合有清晰的层级结构时，可通过级联选择器逐级查看并选择。

### 3.2.6、Switch 开关

表示两种相互对立的状态间的切换，多用于触发「开/关」。

### 3.2.7、Slider 滑块

通过拖动滑块在一个固定区间内进行选择

### 3.2.8、TimePicker 时间选择器

用于选择或输入日期

### 3.2.9、DatePicker 日期选择器

用于选择或输入日期

基本单位由type属性指定。快捷选项需配置picker-options对象中的shortcuts，禁用日期通过 disabledDate 设置，传入函数
```html

​```html
<html>

<head>
    <meta charset="utf-8">
    <title>Layout 布局-基础布局</title>
    <link rel="stylesheet" href="https://unpkg.com/element-ui/lib/theme-chalk/index.css">
    <link rel="stylesheet" href="https://unpkg.com/element-ui/lib/theme-chalk/display.css">
    <!-- 导入Vue -->
    <script src="https://unpkg.com/vue/dist/vue.js"></script>
    <!-- 引入组件库 -->
    <script src="https://unpkg.com/element-ui/lib/index.js"></script>
</head>
<style>
</style>

<body>
<div id="app">
    <template>   <div class="block">
            <span class="demonstration">默认</span>
            <el-date-picker
                    v-model="value1"
                    type="date"
                    placeholder="选择日期">
            </el-date-picker>
        </div>
        <br>
        <div class="block">
            <span class="demonstration">带快捷选项</span>
            <el-date-picker
                    v-model="value2"
                    align="right"
                    type="date"
                    placeholder="选择日期"
                    :picker-options="pickerOptions">
            </el-date-picker>
        </div>
    </template>
</div>
</body>
<script>
    new Vue({
        el: '#app',
        data() {
            return {
                pickerOptions: {
                    disabledDate(time) {
                        return time.getTime() > Date.now();
                    },
                    shortcuts: [{
                        text: '今天',
                        onClick(picker) {
                            picker.$emit('pick', new Date());
                        }
                    }, {
                        text: '昨天',
                        onClick(picker) {
                            const date = new Date();
                            date.setTime(date.getTime() - 3600 * 1000 * 24);
                            picker.$emit('pick', date);
                        }
                    }, {
                        text: '一周前',
                        onClick(picker) {
                            const date = new Date();
                            date.setTime(date.getTime() - 3600 * 1000 * 24 * 7);
                            picker.$emit('pick', date);
                        }
                    }]
                },
                value1: '',
                value2: '',
            };
        }
    })
</script>

```
### 3.2.10、DateTimePicker 日期时间选择器
```html
<div id="app">
    <template>
        <div class="block">
            <span class="demonstration">默认</span>
            <el-date-picker
                    v-model="value1"
                    type="datetime"
                    placeholder="选择日期时间">
            </el-date-picker>
        </div>
        <div class="block">
            <span class="demonstration">带快捷选项</span>
            <el-date-picker
                    v-model="value2"
                    type="datetime"
                    placeholder="选择日期时间"
                    align="right"
                    :picker-options="pickerOptions">
            </el-date-picker>
        </div>
        <div class="block">
            <span class="demonstration">设置默认时间</span>
            <el-date-picker
                    v-model="value3"
                    type="datetime"
                    placeholder="选择日期时间"
                    default-time="12:00:00">
            </el-date-picker>
        </div>
    </template>
</div>
</body>
<script>
    new Vue({
        el: '#app',
        data() {
            return {
                pickerOptions: {
                    shortcuts: [{
                        text: '今天',
                        onClick(picker) {
                            picker.$emit('pick', new Date());
                        }
                    }, {
                        text: '昨天',
                        onClick(picker) {
                            const date = new Date();
                            date.setTime(date.getTime() - 3600 * 1000 * 24);
                            picker.$emit('pick', date);
                        }
                    }, {
                        text: '一周前',
                        onClick(picker) {
                            const date = new Date();
                            date.setTime(date.getTime() - 3600 * 1000 * 24 * 7);
                            picker.$emit('pick', date);
                        }
                    }]
                },
                value1: '',
                value2: '',
                value3: ''
            };
        }
    })
</script>

```
### 3.2.11、Upload 上传

通过点击或者拖拽上传文件

### 3.2.12、Rate 评分

评分组件

### 3.2.13、ColorPicker 颜色选择器

用于颜色选择，支持多种格式。

### 3.2.14、Transfer 穿梭框

### 3.2.15、Form 表单

由输入框、选择器、单选框、多选框等控件组成，用以收集、校验、提交数据


W3C 标准中有如下规定：

When there is only one single-line text input field in a form, the user agent should accept Enter in that field as a request to submit the form.

即：当一个 form 元素中只有一个输入框时，在该输入框中按下回车应提交该表单。如果希望阻止这一默认行为，可以在\<el-form>标签上添加 @submit.native.prevent。

```html
<html>

<head>
    <meta charset="utf-8">
    <title>Layout 布局-基础布局</title>
    <link rel="stylesheet" href="https://unpkg.com/element-ui/lib/theme-chalk/index.css">
    <link rel="stylesheet" href="https://unpkg.com/element-ui/lib/theme-chalk/display.css">
    <!-- 导入Vue -->
    <script src="https://unpkg.com/vue/dist/vue.js"></script>
    <!-- 引入组件库 -->
    <script src="https://unpkg.com/element-ui/lib/index.js"></script>
</head>
<style>
    .el-form{
        width: 400px;
    }
</style>

<body>
<div id="app">
    <el-form ref="form" :model="form" label-width="80px" class="el-form">
        <el-form-item label="活动名称">
            <el-input v-model="form.name"></el-input>
        </el-form-item>
        <el-form-item label="活动区域">
            <el-select v-model="form.region" placeholder="请选择活动区域">
                <el-option label="区域一" value="shanghai"></el-option>
                <el-option label="区域二" value="beijing"></el-option>
            </el-select>
        </el-form-item>
        <el-form-item label="活动时间">
            <el-col :span="11">
                <el-date-picker type="date" placeholder="选择日期" v-model="form.date1" style="width: 100%;"></el-date-picker>
            </el-col>
            <el-col class="line" :span="2">-</el-col>
            <el-col :span="11">
                <el-time-picker placeholder="选择时间" v-model="form.date2" style="width: 100%;"></el-time-picker>
            </el-col>
        </el-form-item>
        <el-form-item label="即时配送">
            <el-switch v-model="form.delivery"></el-switch>
        </el-form-item>
        <el-form-item label="活动性质">
            <el-checkbox-group v-model="form.type">
                <el-checkbox label="美食/餐厅线上活动" name="type"></el-checkbox>
                <el-checkbox label="地推活动" name="type"></el-checkbox>
                <el-checkbox label="线下主题活动" name="type"></el-checkbox>
                <el-checkbox label="单纯品牌曝光" name="type"></el-checkbox>
            </el-checkbox-group>
        </el-form-item>
        <el-form-item label="特殊资源">
            <el-radio-group v-model="form.resource">
                <el-radio label="线上品牌商赞助"></el-radio>
                <el-radio label="线下场地免费"></el-radio>
            </el-radio-group>
        </el-form-item>
        <el-form-item label="活动形式">
            <el-input type="textarea" v-model="form.desc"></el-input>
        </el-form-item>
        <el-form-item>
            <el-button type="primary" @click="onSubmit">立即创建</el-button>
            <el-button>取消</el-button>
        </el-form-item>
    </el-form>
</div>
</body>
<script>
    new Vue({
        el: '#app',
        data() {
            return {
                form: {
                    name: '',
                    region: '',
                    date1: '',
                    date2: '',
                    delivery: false,
                    type: [],
                    resource: '',
                    desc: ''
                }
            }
        },
        methods: {
            onSubmit() {
                console.log('submit!');
            }
        }
    })
</script>

```
## 3.3、数据(data)组件

### 3.3.1、Table 表格

用于展示多条结构类似的数据，可对数据进行排序、筛选、对比或其他自定义操作。

当\<el-table>元素中注入data对象数组后，在\<el-table-column>中用prop属性来对应对象中的键名即可填入数据，用label属性来定义表格的列名。可以使用width属性来定义列宽。

```html
<html>
<head>
    <meta charset="utf-8">
    <title>Layout 布局-基础布局</title>
    <link rel="stylesheet" href="https://unpkg.com/element-ui/lib/theme-chalk/index.css">
    <link rel="stylesheet" href="https://unpkg.com/element-ui/lib/theme-chalk/display.css">
    <!-- 导入Vue -->
    <script src="https://unpkg.com/vue/dist/vue.js"></script>
    <!-- 引入组件库 -->
    <script src="https://unpkg.com/element-ui/lib/index.js"></script>
</head>
<style>
    .el-form{
        width: 400px;
    }
</style>

<body>
<div id="app">
    <template>
        <el-table
                :data="tableData"
                style="width: 100%">
            <el-table-column
                    prop="date"
                    label="日期"
                    width="180">
            </el-table-column>
            <el-table-column
                    prop="name"
                    label="姓名"
                    width="180">
            </el-table-column>
            <el-table-column
                    prop="address"
                    label="地址">
            </el-table-column>
        </el-table>
    </template>
</div>
</body>
<script>
    new Vue({
        el: '#app',
        data() {
            return {
                tableData: [{
                    date: '2016-05-02',
                    name: '王小虎',
                    address: '上海市普陀区金沙江路 1518 弄'
                }, {
                    date: '2016-05-04',
                    name: '王小虎',
                    address: '上海市普陀区金沙江路 1517 弄'
                }, {
                    date: '2016-05-01',
                    name: '王小虎',
                    address: '上海市普陀区金沙江路 1519 弄'
                }, {
                    date: '2016-05-03',
                    name: '王小虎',
                    address: '上海市普陀区金沙江路 1516 弄'
                }]
            }
        }
    })
</script>
```
### 3.3.2、Tag 标签

用于标记和选择。

### 3.3.3、Progress 进度条

用于展示操作进度，告知用户当前状态和预期。

### 3.3.4、Tree 树形控件

用清晰的层级结构展示信息，可展开或折叠。

### 3.3.5、Pagination 分页

当数据量过多时，使用分页分解数据。

### 3.3.6、Badge 标记

出现在按钮、图标旁的数字或状态标记。

## 3.4、Notice组件

### 3.4.1、Alert 警告

用于页面中展示重要的提示信息。

```html
<el-alert title="消息提示的文案" type="info"> </el-alert>
<el-alert title="警告提示的文案" type="warning"> </el-alert> 
<el-alert title="错误提示的文案" type="error"> </el-alert>
```


### 3.4.2、Loading 加载

加载数据时显示动效。

### 3.4.3、Message 消息提示

常用于主动操作后的反馈提示。与 Notification 的区别是后者更多用于系统级通知的被动提醒。

### 3.4.4、MessageBox 弹框

模拟系统的消息提示框而实现的一套模态对话框组件，用于消息提示、确认消息和提交内容。


调用$alert方法即可打开消息提示，它模拟了系统的 alert，无法通过按下 ESC 或点击框外关闭。此例中接收了两个参数，message和title。值得一提的是，窗口被关闭后，它默认会返回一个Promise对象便于进行后续操作的处理。若不确定浏览器是否支持Promise，可自行引入第三方 polyfill 或像本例一样使用回调进行后续处理。
```html
<el-button type="text" @click="open">点击打开 Message Box</el-button>
<script>
    new Vue ({
        el: '#app',
        methods: {
            open() {
                this.$alert('这是一段内容', '标题名称', {
                    confirmButtonText: '确定',
                    callback: action => {
                        this.$message({
                            type: 'info',
                            message: `action: ${ action }`
                        });
                    }
                });
            }
        }
    })
</script>
```
### 3.4.5、Notification 通知

悬浮出现在页面角落，显示全局的通知提醒消息。

## 3.5、Navigation组件

### 3.5.1、NavMenu 导航菜单

为网站提供导航功能的菜单。

导航菜单默认为垂直模式，通过`mode`属性可以使导航菜单变更为水平模式。另外，在菜单中通过`submenu`组件可以生成二级菜单。Menu 还提供了`background-color`、`text-color`和`active-text-color`，分别用于设置菜单的背景色、菜单的文字颜色和当前激活菜单的文字颜色。

#### 3.5.1.1、顶栏

示例代码：

```vue
<el-menu :default-active="activeIndex" class="el-menu-demo" mode="horizontal" @select="handleSelect">
  <el-menu-item index="1">处理中心</el-menu-item>
  <el-submenu index="2">
    <template slot="title">我的工作台</template>
    <el-menu-item index="2-1">选项1</el-menu-item>
    <el-menu-item index="2-2">选项2</el-menu-item>
    <el-menu-item index="2-3">选项3</el-menu-item>
    <el-submenu index="2-4">
      <template slot="title">选项4</template>
      <el-menu-item index="2-4-1">选项1</el-menu-item>
      <el-menu-item index="2-4-2">选项2</el-menu-item>
      <el-menu-item index="2-4-3">选项3</el-menu-item>
    </el-submenu>
  </el-submenu>
  <el-menu-item index="3" disabled>消息中心</el-menu-item>
  <el-menu-item index="4"><a href="https://www.ele.me" target="_blank">订单管理</a></el-menu-item>
</el-menu>
<div class="line"></div>
<el-menu
  :default-active="activeIndex2"
  class="el-menu-demo"
  mode="horizontal"
  @select="handleSelect"
  background-color="#545c64"
  text-color="#fff"
  active-text-color="#ffd04b">
  <el-menu-item index="1">处理中心</el-menu-item>
  <el-submenu index="2">
    <template slot="title">我的工作台</template>
    <el-menu-item index="2-1">选项1</el-menu-item>
    <el-menu-item index="2-2">选项2</el-menu-item>
    <el-menu-item index="2-3">选项3</el-menu-item>
    <el-submenu index="2-4">
      <template slot="title">选项4</template>
      <el-menu-item index="2-4-1">选项1</el-menu-item>
      <el-menu-item index="2-4-2">选项2</el-menu-item>
      <el-menu-item index="2-4-3">选项3</el-menu-item>
    </el-submenu>
  </el-submenu>
  <el-menu-item index="3" disabled>消息中心</el-menu-item>
  <el-menu-item index="4"><a href="https://www.ele.me" target="_blank">订单管理</a></el-menu-item>
</el-menu>

<script>
  export default {
    data() {
      return {
        activeIndex: '1',
        activeIndex2: '1'
      };
    },
    methods: {
      handleSelect(key, keyPath) {
        console.log(key, keyPath);
      }
    }
  }
</script>
```

#### 3.5.1.2、侧栏

通过`el-menu-item-group`组件可以实现菜单进行分组，分组名可以通过`title`属性直接设定，也可以通过具名 slot 来设定。

```vue
<el-row class="tac">
  <el-col :span="12">
    <h5>默认颜色</h5>
    <el-menu
      default-active="2"
      class="el-menu-vertical-demo"
      @open="handleOpen"
      @close="handleClose">
      <el-submenu index="1">
        <template slot="title">
          <i class="el-icon-location"></i>
          <span>导航一</span>
        </template>
        <el-menu-item-group>
          <template slot="title">分组一</template>
          <el-menu-item index="1-1">选项1</el-menu-item>
          <el-menu-item index="1-2">选项2</el-menu-item>
        </el-menu-item-group>
        <el-menu-item-group title="分组2">
          <el-menu-item index="1-3">选项3</el-menu-item>
        </el-menu-item-group>
        <el-submenu index="1-4">
          <template slot="title">选项4</template>
          <el-menu-item index="1-4-1">选项1</el-menu-item>
        </el-submenu>
      </el-submenu>
      <el-menu-item index="2">
        <i class="el-icon-menu"></i>
        <span slot="title">导航二</span>
      </el-menu-item>
      <el-menu-item index="3" disabled>
        <i class="el-icon-document"></i>
        <span slot="title">导航三</span>
      </el-menu-item>
      <el-menu-item index="4">
        <i class="el-icon-setting"></i>
        <span slot="title">导航四</span>
      </el-menu-item>
    </el-menu>
  </el-col>
  <el-col :span="12">
    <h5>自定义颜色</h5>
    <el-menu
      default-active="2"
      class="el-menu-vertical-demo"
      @open="handleOpen"
      @close="handleClose"
      background-color="#545c64"
      text-color="#fff"
      active-text-color="#ffd04b">
      <el-submenu index="1">
        <template slot="title">
          <i class="el-icon-location"></i>
          <span>导航一</span>
        </template>
        <el-menu-item-group>
          <template slot="title">分组一</template>
          <el-menu-item index="1-1">选项1</el-menu-item>
          <el-menu-item index="1-2">选项2</el-menu-item>
        </el-menu-item-group>
        <el-menu-item-group title="分组2">
          <el-menu-item index="1-3">选项3</el-menu-item>
        </el-menu-item-group>
        <el-submenu index="1-4">
          <template slot="title">选项4</template>
          <el-menu-item index="1-4-1">选项1</el-menu-item>
        </el-submenu>
      </el-submenu>
      <el-menu-item index="2">
        <i class="el-icon-menu"></i>
        <span slot="title">导航二</span>
      </el-menu-item>
      <el-menu-item index="3" disabled>
        <i class="el-icon-document"></i>
        <span slot="title">导航三</span>
      </el-menu-item>
      <el-menu-item index="4">
        <i class="el-icon-setting"></i>
        <span slot="title">导航四</span>
      </el-menu-item>
    </el-menu>
  </el-col>
</el-row>

<script>
  export default {
    methods: {
      handleOpen(key, keyPath) {
        console.log(key, keyPath);
      },
      handleClose(key, keyPath) {
        console.log(key, keyPath);
      }
    }
  }
</script>
```

#### 3.5.1.3、折叠

```vue
<el-radio-group v-model="isCollapse" style="margin-bottom: 20px;">
  <el-radio-button :label="false">展开</el-radio-button>
  <el-radio-button :label="true">收起</el-radio-button>
</el-radio-group>
<el-menu default-active="1-4-1" class="el-menu-vertical-demo" @open="handleOpen" @close="handleClose" :collapse="isCollapse">
  <el-submenu index="1">
    <template slot="title">
      <i class="el-icon-location"></i>
      <span slot="title">导航一</span>
    </template>
    <el-menu-item-group>
      <span slot="title">分组一</span>
      <el-menu-item index="1-1">选项1</el-menu-item>
      <el-menu-item index="1-2">选项2</el-menu-item>
    </el-menu-item-group>
    <el-menu-item-group title="分组2">
      <el-menu-item index="1-3">选项3</el-menu-item>
    </el-menu-item-group>
    <el-submenu index="1-4">
      <span slot="title">选项4</span>
      <el-menu-item index="1-4-1">选项1</el-menu-item>
    </el-submenu>
  </el-submenu>
  <el-menu-item index="2">
    <i class="el-icon-menu"></i>
    <span slot="title">导航二</span>
  </el-menu-item>
  <el-menu-item index="3" disabled>
    <i class="el-icon-document"></i>
    <span slot="title">导航三</span>
  </el-menu-item>
  <el-menu-item index="4">
    <i class="el-icon-setting"></i>
    <span slot="title">导航四</span>
  </el-menu-item>
</el-menu>

<style>
  .el-menu-vertical-demo:not(.el-menu--collapse) {
    width: 200px;
    min-height: 400px;
  }
</style>

<script>
  export default {
    data() {
      return {
        isCollapse: true
      };
    },
    methods: {
      handleOpen(key, keyPath) {
        console.log(key, keyPath);
      },
      handleClose(key, keyPath) {
        console.log(key, keyPath);
      }
    }
  }
</script>
```



### 3.5.2、Tabs 标签页

分隔内容上有关联但属于不同类别的数据集合。

```html

<style>
    .tac{
        width: 500px;
    }

</style>

<body>
<div id="app">
    <template>
        <el-tabs v-model="activeName" @tab-click="handleClick" class="tac">
            <el-tab-pane label="用户管理" name="first">用户管理</el-tab-pane>
            <el-tab-pane label="配置管理" name="second">配置管理</el-tab-pane>
            <el-tab-pane label="角色管理" name="third">角色管理</el-tab-pane>
            <el-tab-pane label="定时任务补偿" name="fourth">定时任务补偿</el-tab-pane>
        </el-tabs>
    </template>
</div>
</body>
<script>
    new Vue({
        el: '#app',
        data() {
            return {
                activeName: 'second'
            };
        },
        methods: {
            handleClick(tab, event) {
                console.log(tab, event);
            }
        }
    })
</script>

```
### 3.5.3、Breadcrumb 面包屑

显示当前页面的路径，快速返回之前的任意页面。

### 3.5.4、PageHeader 页头

如果页面的路径比较简单，推荐使用页头组件而非面包屑组件。

### 3.5.5、Dropdown 下拉菜单

将动作或菜单折叠到下拉菜单中。

移动到下拉菜单上，展开更多操作。

```html
<div id="app">
    <el-dropdown>
      <span class="el-dropdown-link">
        下拉菜单<i class="el-icon-arrow-down el-icon--right"></i>
      </span>
        <el-dropdown-menu slot="dropdown">
            <el-dropdown-item>黄金糕</el-dropdown-item>
            <el-dropdown-item>狮子头</el-dropdown-item>
            <el-dropdown-item>螺蛳粉</el-dropdown-item>
            <el-dropdown-item disabled>双皮奶</el-dropdown-item>
            <el-dropdown-item divided>蚵仔煎</el-dropdown-item>
        </el-dropdown-menu>
    </el-dropdown>
</div>
```

### 3.5.6、Steps 步骤条

引导用户按照流程完成任务的分步导航条，可根据实际应用场景设定步骤，步骤不得少于 2 步。

设置active属性，接受一个Number，表明步骤的 index，从 0 开始。需要定宽的步骤条时，设置space属性即可，它接受Boolean，单位为px，如果不设置，则为自适应。设置finish-status属性可以改变已经完成的步骤的状态。

```html
<body>
<div id="app">
    <el-steps :active="active" finish-status="success" class="step">
        <el-step title="步骤 1"></el-step>
        <el-step title="步骤 2"></el-step>
        <el-step title="步骤 3"></el-step>
    </el-steps>
    <el-button style="margin-top: 12px;" @click="next">下一步</el-button>

</div>
</body>
<script>
    new Vue({
        el: '#app',
        data() {
            return {
                active: 0
            };
        },

        methods: {
            next() {
                if (this.active++ > 2) this.active = 0;
            }
        }
    })
</script>
```
## 3.6、其他组件

### 3.6.1、Dialog 对话框

在保留当前页面状态的情况下，告知用户并承载相关操作。

Dialog 弹出一个对话框，适合需要定制性更大的场景。

before-close 仅当用户通过点击关闭图标或遮罩关闭 Dialog 时起效。如果你在 footer 具名 slot 里添加了用于关闭 Dialog 的按钮，那么可以在按钮的点击回调函数里加入 before-close 的相关逻辑。

```html
<div id="app">
    <el-button type="text" @click="dialogVisible = true">点击打开 Dialog</el-button>

    <el-dialog
            title="提示"
            :visible.sync="dialogVisible"
            width="30%"
            :before-close="handleClose">
        <span>这是一段信息</span>
        <span slot="footer" class="dialog-footer">
    <el-button @click="dialogVisible = false">取 消</el-button>
    <el-button type="primary" @click="dialogVisible = false">确 定</el-button>
  </span>
    </el-dialog>
</div>
</body>
<script>
    new Vue({
        el: '#app',
        data() {
            return {
                dialogVisible: false
            };
        },
        methods: {
            handleClose(done) {
                this.$confirm('确认关闭？')
                    .then(_ => {
                        done();
                    })
                    .catch(_ => {});
            }
        }
    })
</script>

```
### 3.6.2、Tooltip 文字提示

常用于展示鼠标 hover 时的提示信息。

基础用法

在这里我们提供 9 种不同方向的展示方式，可以通过以下完整示例来理解，选择你要的效果。

使用content属性来决定hover时的提示信息。由placement属性决定展示效果：placement属性值为：方向-对齐位置；四个方向：top、left、right、bottom；三种对齐位置：start, end，默认为空。如placement="left-end"，则提示信息出现在目标元素的左侧，且提示信息的底部与目标元素的底部对齐。

```html  
<div id="app">
    <div class="box">
        <br><br><br><br><br>
        <div class="top">
            <el-tooltip class="item" effect="dark" content="Top Left 提示文字" placement="top-start">
                <el-button>上左</el-button>
            </el-tooltip>
            <el-tooltip class="item" effect="dark" content="Top Center 提示文字" placement="top">
                <el-button>上边</el-button>
            </el-tooltip>
            <el-tooltip class="item" effect="dark" content="Top Right 提示文字" placement="top-end">
                <el-button>上右</el-button>
            </el-tooltip>
        </div>
        <br><br><br><br><br>
        <div class="left">
            <el-tooltip class="item" effect="dark" content="Left Top 提示文字" placement="left-start">
                <el-button>左上</el-button>
            </el-tooltip>
            <el-tooltip class="item" effect="dark" content="Left Center 提示文字" placement="left">
                <el-button>左边</el-button>
            </el-tooltip>
            <el-tooltip class="item" effect="dark" content="Left Bottom 提示文字" placement="left-end">
                <el-button>左下</el-button>
            </el-tooltip>
        </div>
        <br><br><br><br><br>
        <div class="right">
            <el-tooltip class="item" effect="dark" content="Right Top 提示文字" placement="right-start">
                <el-button>右上</el-button>
            </el-tooltip>
            <el-tooltip class="item" effect="dark" content="Right Center 提示文字" placement="right">
                <el-button>右边</el-button>
            </el-tooltip>
            <el-tooltip class="item" effect="dark" content="Right Bottom 提示文字" placement="right-end">
                <el-button>右下</el-button>
            </el-tooltip>
        </div>
        <br><br><br><br><br>
        <div class="bottom">
            <el-tooltip class="item" effect="dark" content="Bottom Left 提示文字" placement="bottom-start">
                <el-button>下左</el-button>
            </el-tooltip>
            <el-tooltip class="item" effect="dark" content="Bottom Center 提示文字" placement="bottom">
                <el-button>下边</el-button>
            </el-tooltip>
            <el-tooltip class="item" effect="dark" content="Bottom Right 提示文字" placement="bottom-end">
                <el-button>下右</el-button>
            </el-tooltip>
        </div>
    </div>
</div>

```
### 3.6.3、Popover 弹出框

Popover 的属性与 Tooltip 很类似，它们都是基于Vue-popper开发的，因此对于重复属性，请参考 Tooltip 的文档，在此文档中不做详尽解释。

trigger属性用于设置何时触发 Popover，支持四种触发方式：hover，click，focus 和 manual。对于触发 Popover 的元素，有两种写法：使用 slot="reference" 的具名插槽，或使用自定义指令v-popover指向 Popover 的索引ref。

```html



<body>
<div id="app">
    <template>
        <el-popover
                placement="top-start"
                title="标题"
                width="200"
                trigger="hover"
                content="这是一段内容,这是一段内容,这是一段内容,这是一段内容。">
            <el-button slot="reference">hover 激活</el-button>
        </el-popover>

        <el-popover
                placement="bottom"
                title="标题"
                width="200"
                trigger="click"
                content="这是一段内容,这是一段内容,这是一段内容,这是一段内容。">
            <el-button slot="reference">click 激活</el-button>
        </el-popover>
    
        <el-popover
                ref="popover"
                placement="right"
                title="标题"
                width="200"
                trigger="focus"
                content="这是一段内容,这是一段内容,这是一段内容,这是一段内容。">
        </el-popover>
        <el-button v-popover:popover>focus 激活</el-button>
    
        <el-popover
                placement="bottom"
                title="标题"
                width="200"
                trigger="manual"
                content="这是一段内容,这是一段内容,这是一段内容,这是一段内容。"
                v-model="visible">
            <el-button slot="reference" @click="visible = !visible">手动激活</el-button>
        </el-popover>
    </template>
</div>
</body>
<script>
    new Vue({
        el: '#app',
        data() {
            return {
                visible: false
            };
        }
    })
</script>

```
### 3.6.4、Card 卡片

将信息聚合在卡片容器中展示。

### 3.6.5、Carousel 走马灯(轮播图)

在有限空间内，循环播放同一类型的图片、文字等内容

```html

<style>
    .el-carousel__item h3 {
        color: #475669;
        font-size: 14px;
        opacity: 0.75;
        line-height: 150px;
        margin: 0;
    }

    .el-carousel__item:nth-child(2n) {
        background-color: #99a9bf;
    }
    
    .el-carousel__item:nth-child(2n+1) {
        background-color: #d3dce6;
    }
</style>

<body>
<div id="app">
    <template>
        <div class="block">
            <span class="demonstration">默认 Hover 指示器触发</span>
            <el-carousel height="150px">
                <el-carousel-item v-for="item in 4" :key="item">
                    <h3 class="small">{{ item }}</h3>
                </el-carousel-item>
            </el-carousel>
        </div>
        <div class="block">
            <span class="demonstration">Click 指示器触发</span>
            <el-carousel trigger="click" height="150px">
                <el-carousel-item v-for="item in 4" :key="item">
                    <h3 class="small">{{ item }}</h3>
                </el-carousel-item>
            </el-carousel>
        </div>
    </template>
</div>
</body>
<script>
    new Vue({
        el: '#app'
    })
</script>

```
### 3.6.6、Collapse 折叠面板

通过折叠面板收纳内容区域

### 3.6.7、Timeline 时间线

可视化地呈现时间流信息。

Timeline 可拆分成多个按照时间戳正序或倒序排列的 activity，时间戳是其区分于其他控件的重要特征，使⽤时注意与 Steps 步骤条等区分。


```html
<div id="app">
    <div class="block">
        <div class="radio">
            排序：
            <el-radio-group v-model="reverse">
                <el-radio :label="true">倒序</el-radio>
                <el-radio :label="false">正序</el-radio>
            </el-radio-group>
        </div>

        <el-timeline :reverse="reverse">
            <el-timeline-item
                    v-for="(activity, index) in activities"
                    :key="index"
                    :timestamp="activity.timestamp">
                {{activity.content}}
            </el-timeline-item>
        </el-timeline>
    </div>
</div>
<script>
    new Vue({
        el: '#app',
        data() {
            return {
                reverse: true,
                activities: [{
                    content: '活动按期开始',
                    timestamp: '2018-04-15'
                }, {
                    content: '通过审核',
                    timestamp: '2018-04-13'
                }, {
                    content: '创建成功',
                    timestamp: '2018-04-11'
                }]
            };
        }
    })
</script>
```
### 3.6.8、Divider 分割线

区隔内容的分割线。

### 3.6.9、Calendar calendar

显示日期

### 3.6.10、Image 图片

图片容器，在保留原生img的特性下，支持懒加载，自定义占位、加载失败等

可通过fit确定图片如何适应到容器框，同原生 object-fit。

```html

<style>

</style>

<body>
<div id="app">
    <div class="demo-image">
        <div class="block" v-for="fit in fits" :key="fit">
            <span class="demonstration">{{ fit }}</span>
            <el-image
                    style="width: 100px; height: 100px"
                    :src="url"
                    :fit="fit"></el-image>
        </div>
    </div>
</div>
</body>
<script>
    new Vue({
        el: '#app',
        data() {
            return {
                fits: ['fill', 'contain', 'cover', 'none', 'scale-down'],
                url: 'https://fuss10.elemecdn.com/e/5d/4a731a90594a4af544c0c25941171jpeg.jpeg'
            }
        }
    })
</script>

```
### 3.6.11、Backtop 回到顶部

返回页面顶部的操作按钮

### 3.6.12、InfiniteScroll 无限滚动

滚动至底部时，加载更多数据。

### 3.6.13、autocomplete自动补全输入框

autocomplete是input组件的一个分支，专门用来处理模糊匹配的相关知识

```vue
<template>
  <el-row class="demo-autocomplete">
    <el-col :span="12">
      <div class="sub-title my-2 text-sm text-gray-600">
        list suggestions when activated
      </div>
      <el-autocomplete
        v-model="state1"
        :fetch-suggestions="querySearch"
        clearable
        class="inline-input w-50"
        placeholder="Please Input"
        @select="handleSelect"
      />
    </el-col>
    <el-col :span="12">
      <div class="sub-title my-2 text-sm text-gray-600">
        list suggestions on input
      </div>
      <el-autocomplete
        v-model="state2"
        :fetch-suggestions="querySearch"
        :trigger-on-focus="false"
        clearable
        class="inline-input w-50"
        placeholder="Please Input"
        @select="handleSelect"
      />
    </el-col>
  </el-row>
</template>

<script lang="ts" setup>
import { onMounted, ref } from 'vue'

interface RestaurantItem {
  value: string
  link: string
}

const state1 = ref('')
const state2 = ref('')

const restaurants = ref<RestaurantItem[]>([])
const querySearch = (queryString: string, cb: any) => {
  const results = queryString
    ? restaurants.value.filter(createFilter(queryString))
    : restaurants.value
  // call callback function to return suggestions
  cb(results)
}
const createFilter = (queryString: string) => {
  return (restaurant: RestaurantItem) => {
    return (
      restaurant.value.toLowerCase().indexOf(queryString.toLowerCase()) === 0
    )
  }
}
const loadAll = () => {
  return [
    { value: 'vue', link: 'https://github.com/vuejs/vue' },
    { value: 'element', link: 'https://github.com/ElemeFE/element' },
    { value: 'cooking', link: 'https://github.com/ElemeFE/cooking' },
    { value: 'mint-ui', link: 'https://github.com/ElemeFE/mint-ui' },
    { value: 'vuex', link: 'https://github.com/vuejs/vuex' },
    { value: 'vue-router', link: 'https://github.com/vuejs/vue-router' },
    { value: 'babel', link: 'https://github.com/babel/babel' },
  ]
}

const handleSelect = (item: RestaurantItem) => {
  console.log(item)
}

onMounted(() => {
  restaurants.value = loadAll()
})
</script>

```

