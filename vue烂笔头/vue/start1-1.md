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

### axios的使用

1. 封装方法

    ```
        // 接口文件
        import axios from 'axios';
        // axios.defaults.baseURL = 'http://localhost:3000' // 增加默认请求路径
        
        // axios 数据拦截处理
        axios.interceptors.response.use((res) => {
          return res.data
        })
        
        // 获取活动列表数据
        export let getData = (url,params) => {
          return axios.post(url, params);
          // return axios.get("https://www.easy-mock.com/mock/5b7660bb76a41b2c09dbf28b/pcActiveList/pcActiveList#!method=get");
        };
    ```

2. 具体使用
    
    ```
     // 地区数据解构
    import { getData } from "../../api/index.js";   
    
    // 省份数据
    getData("http://120.131.6.133:8086/org/admDivision",paramsShen).then(
      function(data) {
        // console.log(data);
        if (data.status) {
          // 清空数据
          _this.cityList = [];

          var list = data.info;
          list.forEach(function(e, i) {
            _this.cityList.push({
              value: e.id,
              label: e.name
            });
          });
        }
      },
      function(error) {
        console.log(error);
      }
    );
    
    ```


