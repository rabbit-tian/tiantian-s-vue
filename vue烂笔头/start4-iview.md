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

#### iview 中日期选择器的使用
1. 配置项
    - editable： 文本框是否可以输入，只在没有使用 slot 时有效
    

```
<DatePicker :editable="false" size="large" type="date" placeholder="开始时间" v-model="date" :options="optDate"></DatePicker>
<DatePicker :editable="false" size="large" type="date" placeholder="结束时间" v-model="endDate" :options="optDate2"></DatePicker>

 data() {
    return {
      // 设置不可用日期
      optDate: {
        disabledDate (date) {
            return date && date.valueOf() < Date.now() - 86400000*2;
        }
      },
      optDate2: {
        disabledDate (date) {
          return date && date.valueOf() < Date.now() - 86400000;
        }
      },
    }
 }
```

