### 安装iview
1. `npm install iview --save`

2. 在 main.js 中引入即可使用
    - `import iView from 'iview';`
    - `import 'iview/dist/styles/iview.css';`
    - `Vue.use(iView);`
    


#### iview 中 tabs 和路由结合的使用

1. 废话不多说，直接上代码

```
 <div class="head">
    <Tabs @on-click="tabSelect">
        <TabPane label="公共活动统计" name="0"></TabPane>
        <TabPane label="机构活动统计" name="1"></TabPane>
    </Tabs>
</div>
<div class="main">
<router-view></router-view>
</div>


  methods: {
    // 切换路由
    tabSelect (e) {
      if (e == 0) {
        this.$router.push({path:'/home/publicData'});
      }else {
        this.$router.push({path:'/home/organData'});
      }
    }
  }
```

