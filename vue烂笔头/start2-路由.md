### 路由
1. 二级路由永远不加 / 
2. 具体代码展示

    ```
    export default new Router({
      routes: [
        { path: "", component: Home }, // 默认展示的路径
        { path: "/home", component: Home },
        {
          path: "/list",
          component: List,
          children: [
            { path: "", component: Profile }, // 默认展示的路径
            {
              path: "profile",
              component: Profile
            },
            {
              path: "about",
              component: About
            }
          ]
        },
        { path: "*", redirect: "/home" }
      ]
    });
    ```




