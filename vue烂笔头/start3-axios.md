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




