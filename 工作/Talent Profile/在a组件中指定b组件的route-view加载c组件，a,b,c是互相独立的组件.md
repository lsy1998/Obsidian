如果组件 A、B 和 C 是互相独立的组件，则在组件 A 中指定组件 B 的 `<router-view>` 加载组件 C，需要使用命名视图（named views）。

首先，在组件 A 中定义一个路由配置对象，用于加载组件 C：

```javascript
const routes = [
  {
    path: '/component-c',
    name: 'ComponentC',
    components: {
      default: () => import('@/components/ComponentC.vue'),
    },
  },
];
```

其中，`path` 属性指定路由路径，`name` 属性指定路由名称，`components` 属性指定要加载的组件 C，并用命名视图 `default` 将其与 `<router-view>` 组件绑定起来。需要注意的是，组件 C 必须是注册为全局组件或局部组件，并且需要通过动态 `import` 的方式来引入。

然后，在组件 A 的模板中，将 `<router-view>` 组件的 `name` 属性设置为 `component-b`，表示要指定组件 B 的 `<router-view>`：

```html
<template>
  <div>
    <router-view name="component-b" />
  </div>
</template>
```

接着，在组件 B 的路由配置中，也需要为 `<router-view>` 组件指定一个命名视图，以加载组件 C。同时，需要将组件 A 的路由配置和组件 C 的路由配置添加到组件 B 的路由配置中：

```javascript
const routes = [
  {
    path: '/component-b',
    name: 'ComponentB',
    components: {
      default: () => import('@/components/ComponentB.vue'),
      componentC: () => import('@/components/ComponentC.vue'),
    },
    children: [
      ...routesA,
      ...routesC,
    ],
  },
];
```

其中，`components` 属性指定要加载的组件 B 和组件 C，并用命名视图 `componentC` 将组件 C 与 `<router-view>` 组件绑定起来。需要注意的是，组件 B 和组件 C 也必须是注册为全局组件或局部组件，并需要通过动态 `import` 的方式来引入。`children` 属性用于存储组件 A 和组件 C 的路由配置，并添加到组件 B 的路由配置中。

最后，在组件 B 的模板中，使用 `<router-view>` 组件并指定命名视图 `componentC`：

```html
<template>
  <div>
    <h2>Component B</h2>
    <router-view name="componentC" />
  </div>
</template>
```

这样，我们就可以在组件 A 中指定组件 B 的 `<router-view>` 加载组件 C 了，而且组件 A、B 和 C 互不影响，可以单独开发和维护。