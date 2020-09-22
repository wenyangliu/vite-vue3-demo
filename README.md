## Vite+Vue3+Typescript
todoList例子
参考：https://iter01.com/523350.html

### 初始化项目
```
npm create vite-app vite-vue-demo
cd vite-vue-demo
yarn
yarn dev
```

### 安装配置
```
yarn add vue-router@next vuex@next
yarn add typescript -D

main.js 改为 main.ts
修改 .vue 里的script标签
<script lang="ts"></script>
修改index.html 引用 .main.js => main.ts
根目录 新建 shim.d.ts
....
....
```
