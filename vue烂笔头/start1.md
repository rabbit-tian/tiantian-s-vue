### 环境配置
1. 安装脚手架cli
    - npm i -g vue-cli
2. 创建一个基于webpack的新项目
    - vue init webpack smartisan
    
3. 进入文件夹后 ，安装依赖   npm init
4. 安装 vuex  npm i vuex -save
5.  npm i less less-loader --save-dev


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

