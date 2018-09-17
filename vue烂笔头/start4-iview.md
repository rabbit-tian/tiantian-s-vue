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

#### 自定义手机号码验证
1. 参数说明
    - prop="phone": 对应表单域 model 里的字段
    - v-model="formValidate.phone": 验证规则

```
<FormItem label="手机号码" prop="phone">
  <Input v-model="formValidate.phone" placeholder="请输入手机号码" style="width:400px"></Input>
</FormItem>

data () {
    const validatePhone = (rule, value, callback) => {
        if (!value) {
            return callback(new Error('手机号不能为空'));
        } else if (!/^1[34578]\d{9}$/.test(value)) {
            callback('手机号格式不正确');
        } else {
            callback();
        }   
    };


    return {
        formValidate: {
            phone: "", // 手机号码
        },
        ruleValidate:{
            // 手机号码
            phone:[
                {
                    validator:validatePhone,
                    trigger:'blur',
                    required: true,
                    message: "请输入正确的手机号码",
                }
            ],
        }
    }
}
```


#### 全局提示框的使用

```
提示类型 #
不同的提示状态：成功、警告、错误。

<template>
    <Button @click="success">Display success prompt</Button>
    <Button @click="warning">Display warning prompt</Button>
    <Button @click="error">Display error prompt</Button>
</template>
<script>
    export default {
        methods: {
            success () {
                this.$Message.success('This is a success tip');
            },
            warning () {
                this.$Message.warning('This is a warning tip');
            },
            error () {
                this.$Message.error('This is an error tip');
            }
        }
    }
</script>
```

#### Modal 对话框的使用
1. 详细，成功，警告，失败的 提示框

```
<template>
    <Button @click="instance('info')">Info</Button>
    <Button @click="instance('success')">Success</Button>
    <Button @click="instance('warning')">Warning</Button>
    <Button @click="instance('error')">Error</Button>
</template>
<script>
    export default {
        methods: {
            instance (type) {
                const title = 'Title';
                const content = '<p>Content of dialog</p><p>Content of dialog</p>';
                switch (type) {
                    case 'info':
                        this.$Modal.info({
                            title: title,
                            content: content
                        });
                        break;
                    case 'success':
                        this.$Modal.success({
                            title: title,
                            content: content
                        });
                        break;
                    case 'warning':
                        this.$Modal.warning({
                            title: title,
                            content: content
                        });
                        break;
                    case 'error':
                        this.$Modal.error({
                            title: title,
                            content: content
                        });
                        break;
                }
            }
        }
    }
</script>

```


2. 对话框位置
    - 距离顶部20px
    - 垂直居中

```
<style lang="less">
    .vertical-center-modal{
        display: flex;
        align-items: center;
        justify-content: center;

        .ivu-modal{
            top: 0;
        }
    }
</style>
<template>
    <Button @click="modal9 = true">20px from the top</Button>
    <Modal
        title="Title"
        v-model="modal9"
        :styles="{top: '20px'}">
        <p>Content of dialog</p>
        <p>Content of dialog</p>
        <p>Content of dialog</p>
    </Modal>
    <Button @click="modal10 = true">Vertical center</Button>
    <Modal
        title="Title"
        v-model="modal10"
        class-name="vertical-center-modal">
        <p>Content of dialog</p>
        <p>Content of dialog</p>
        <p>Content of dialog</p>
    </Modal>
</template>
<script>
    export default {
        data () {
            return {
                modal9: false,
                modal10: false,
            }
        }
    }
</script>

```

