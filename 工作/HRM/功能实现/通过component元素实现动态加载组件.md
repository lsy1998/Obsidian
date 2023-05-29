
```html
<template>
  <div class="floating-window" :style="style" @mousedown="handleMouseDown" ref="window" v-show="showFloatingWindow">
    <div class="floating-window-header" :style="collapsedStyle">
      <span>{{ title }}</span>
      <i class="el-icon-arrow-down" v-if="!isCollapsed" @click.stop="handleIconClick"></i>
      <i class="el-icon-arrow-up" v-else @click.stop="handleIconClick"></i>
      <i class="el-icon-close" @click.stop="handleIconClose"></i>
    </div>
    <div ref="componentContainer" class="floating-window-content" v-show="!isCollapsed">
    
      <component :is="currentComponent" @hook:mounted="handleComponentMounted"></component>
      
    </div>
  </div>
</template>
```

import是静态的，只能通过require加载组件，且路径要使用模板字符串，且 `@` 和 `.vue` 不能包含在变量里面。**(只针对webpack)**
```js
created() {
    eventBus.$on('showFloatingWindow', (data) => {
      let componentB = null
      this.showFloatingWindow = true
      const pattern = /^@\/|\.vue$/g;
      const componentPath = data.replace(pattern, '')

      componentB = (resolve) => require([`@/${componentPath}.vue`], resolve);

      this.currentComponent = componentB
    })
  },
```
