要在组件 A 中指定组件 B 的 `<router-view>` 加载组件 C，我们可以在组件 A 中定义一个路由对象，并通过组件 B 的路由配置将其加载到 `<router-view>` 中。

首先，在组件 A 中定义一个路由对象，用于加载组件 C：

```javascript
const routes = [
  {
    path: '/component-c',
    name: 'ComponentC',
    component: () => import('@/components/ComponentC.vue'),
  },
];
```

其中，`path` 属性指定路由路径，`name` 属性指定路由名称，`component` 属性指定要加载的组件 C。需要注意的是，组件 C 必须是注册为全局组件或局部组件，并且需要通过动态 `import` 的方式来引入。

然后，在组件 A 的模板中，将 `<router-view>` 组件的 `name` 属性设置为组件 B 的名称，并添加一个路由配置对象，将路由对象映射到组件 B 的路由配置中：

```html
<template>
  <div>
    <router-view :name="componentBName" />
  </div>
</template>

<script>
const routes = [
  // 定义要加载的组件 C 的路由对象
  {
    path: '/component-c',
    name: 'ComponentC',
    component: () => import('@/components/ComponentC.vue'),
  },
];

export default {
  data() {
    return {
      componentBName: 'component-b',
    };
  },
  created() {
    // 将组件 B 的路由配置添加到路由对象中
    this.$router.addRoutes([
      {
        path: '/component-b',
        name: this.componentBName,
        component: () => import('@/components/ComponentB.vue'),
        // 将路由对象映射到组件 B 的路由配置中
        children: routes,
      },
    ]);
  },
};
</script>
```

其中，`this.componentBName` 是组件 B 的名称，用于将该名称映射到组件 B 的路由配置中。`this.$router.addRoutes` 方法用于动态添加路由，将组件 B 的路由配置及其子路由添加到路由表中。最后，需要将 `<router-view>` 组件的 `name` 属性设置为组件 B 的名称，以确保路由能够正确加载到 `<router-view>` 中。

现在，我们就可以在组件 A 中指定组件 B 的 `<router-view>` 加载组件 C 了。在组件 B 的路由配置中也可以添加其他子路由，以扩展组件 B 的功能。
