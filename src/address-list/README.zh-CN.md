# AddressList 地址列表

### 引入

``` javascript
import Vue from 'vue';
import { AddressList } from 'vant';

Vue.use(AddressList);
```

## 代码演示

### 基础用法

```html
<van-address-list
  v-model="chosenAddressId"
  :list="list"
  :disabled-list="disabledList"
  disabled-text="以下地址超出配送范围"
  @add="onAdd"
  @edit="onEdit"
  @delete="onDelete"
  @set-default="onSetDefault"
/>
```

```javascript
export default {
  data() {
    return {
      chosenAddressId: '1',
      list: [
        {
          id: '1',
          name: '张三',
          tel: '13000000000',
          address: '浙江省杭州市西湖区文三路 138 号东方通信大厦 7 楼 501 室'
        },
        {
          id: '2',
          name: '李四',
          tel: '1310000000',
          address: '浙江省杭州市拱墅区莫干山路 50 号'
        }
      ],
      disabledList: [
        {
          id: '3',
          name: '王五',
          tel: '1320000000',
          address: '浙江省杭州市滨江区江南大道 15 号'
        }
      ]
    }
  },

  methods: {
    onAdd() {
      Toast('新增地址');
    },

    onEdit(item, index) {
      Toast('编辑地址:' + index);
    },

    onDelete(item, index) {
      Toast('删除地址:' + index)
    },

    onSetDefault(item, index) {
      Toast('设为默认地址', index)
    }
  }
}
```

## API

### Props

| 参数 | 说明 | 类型 | 默认值 | 版本 |
|------|------|------|------|------|
| v-model | 当前选中地址的 id | *string* | - | - |
| list | 地址列表 | *Address[]* | `[]` | - |
| disabled-list | 不可配送地址列表 | *Address[]* | `[]` | - |
| disabled-text | 不可配送提示文案 | *string* | - | - |
| add-button-text | 底部按钮文字 | *string* | `新增地址` | - |

### Events

| 事件名 | 说明 | 回调参数 |
|------|------|------|------|
| add | 点击新增按钮时触发 | - |
| edit | 点击编辑按钮时触发 | item: 地址对象，index: 索引 |
| delete | 点击删除按钮时触发 | item: 地址对象，index: 索引 |
| select | 切换选中的地址时触发 | item: 地址对象，index: 索引 |
| edit-disabled | 编辑不可配送的地址时触发 | item: 地址对象，index: 索引 |
| select-disabled | 选中不可配送的地址时触发 | item: 地址对象，index: 索引 |
| click-item | 点击任意地址时触发 | item: 地址对象，index: 索引 |
| set-default | 点击设为默认时触发 | item: 地址对象，index: 索引 |

### Address 数据结构

| 键名 | 说明 | 类型 |
|------|------|------|
| id | 每条地址的唯一标识 | *string \| number* |
| name | 收货人姓名 | *string* |
| tel | 收货人手机号 | *string \| number* |
| address | 收货地址 | *string* |

### Slots

| 名称 | 说明 |
|------|------|
| default | 在列表下方插入内容 |
| top | 在顶部插入内容 |
