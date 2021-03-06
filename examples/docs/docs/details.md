## Details

为 PickerView 组件的封装，在其内部构建好日期时间选项。

### 按需引入

```javascript
import Vue from 'vue'
import { DatetimePickerView } from 'buddy-design'

Vue.use(DatetimePickerView)
```

### 基本用法

`v-model` 设置绑定值，默认为 'datetime' 类型，展示年月日时分，绑定值为 `Date` 类型，如果为 'time' 类型，绑定值为字符串。

```html
<wd-datetime-picker-view v-model="value"></wd-datetime-picker-view>

<script>
export default {
  data () {
    return {
      value: new Date()
    }
  }
}
</script>
```

### date 类型

'date' 类型只展示年月日。

```html
<wd-datetime-picker-view type="date" v-model="value"></wd-datetime-picker-view>

<script>
export default {
  data () {
    return {
      value2: ''
    }
  }
}
</script>
```

### year-month 类型

'year-month' 类型只展示年月。

```html
<wd-datetime-picker-view type="year-month" v-model="value"></wd-datetime-picker-view>

<script>
export default {
  data () {
    return {
      value: new Date()
    }
  }
}
</script>
```

### time 类型

'time' 类型只展示时分。

```html
<wd-datetime-picker-view type="time" v-model="value"></wd-datetime-picker-view>

<script>
export default {
  data () {
    return {
      value: '09:20'
    }
  }
}
</script>
```

### 修改弹出层内部格式

给 `formatter` 属性传入一个函数，接收 `type` 和 `value` 值，返回展示的文本内容。`type` 有 `year`、`month`、`date`、`hour`、`minute` 类型，`value` 为 `number` 类型。

```html
<wd-datetime-picker-view v-model="value" :formatter="formatter"></wd-datetime-picker-view>

<script>
export default {
  data () {
    return {
      value: new Date(),
      formatter (type, value) {
        switch (type) {
          case 'year':
            return value + '年'
          case 'month':
            return value + '月'
          case 'date':
            return value + '日'
          case 'hour':
            return value + '时'
          case 'minute':
            return value + '分'
          default:
            return value
        }
      }
    }
  }
}
</script>
```

### 过滤选项

给 `filter` 属性传入一个函数，接收 `type` 和 `values` 值，返回列的选项列表。`type` 有 `year`、`month`、`date`、`hour`、`minute` 类型，`values` 为 number数组。

```html
<wd-datetime-picker-view v-model="value" :filter="filter"></wd-datetime-picker-view>

<script>
export default {
  data () {
    return {
      value: '',
      filter (type, values) {
        if (type === 'minute') {
          return values.filter(value => value % 5 === 0)
        }

        return values
      }
    }
  }
}
</script>
```

### Attributes

| 参数      | 说明                                 | 类型      | 可选值       | 默认值   |
|---------- |------------------------------------ |---------- |------------- |-------- |
| value/v-model | 选中项，当 type 为 time 时，类型为字符串，否则为 Date | string / date | - |
| type | 选择器类型 | string | 'date' / 'year-month' / 'time' | 'datetime' |
| loading | 加载中 | boolean | - | false |
| arrow-html | 是否使用html渲染选择器内容 | boolean | - | true |
| visible-item-count | 展示的行数 | number | - | 7 |
| item-height | 选项高度 | number | - | 33 |
| disabled | 禁用 | boolean | - | fasle |
| readonly | 只读 | boolean | - | false |
| formatter | 自定义弹出层选项文案的格式化函数，返回一个字符串 | function | - | - |
| filter | 自定义过滤选项的函数，返回列的选项数组 | function | - | - |
| minDate | 最小日期 | date | - | 当前日期 - 10年 |
| maxDate | 最大日期 | date | - | 当前日志 + 10年 |
| minHour | 最小小时 | number | - | 0 |
| maxHour | 最大小时 | number | - | 23 |
| minMinute | 最小分钟 | number | - | 0 |
| maxMinute | 最大分钟 | number | - | 59 |

### Events

| 事件名称      | 说明                                 | 参数     |
|------------- |------------------------------------ |--------- |
| change | 选项值修改时触发 | picker实例, 所有列选中项值, 当前列的下标 |
