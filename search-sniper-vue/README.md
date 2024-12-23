# Vue3 项目说明

## 技术栈
- Vue 3
- Vue Router
- Pinia
- Element Plus

## Element Plus使用说明
本项目使用Element Plus作为UI组件库。Element Plus是一个基于Vue3的组件库，提供了丰富的UI组件。

### 使用方法
1. 组件已经全局注册，可以直接在任何组件中使用Element Plus的组件
2. 使用示例：   ```vue
   <template>
     <el-button type="primary">按钮</el-button>
     <el-input v-model="inputValue" placeholder="请输入内容"></el-input>
   </template>   ```

3. 更多组件和用法请参考[Element Plus官方文档](https://element-plus.org/zh-CN/)

## 注意事项
- 确保在使用Element Plus组件时，组件名称前缀为"el-"
- 如果需要使用Element Plus的图标，需要单独安装@element-plus/icons-vue包
