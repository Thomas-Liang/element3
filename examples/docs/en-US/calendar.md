## Calendar

Display date.

### Basic

:::demo Set `value` to specify the currently displayed month. If `value` is not specified, current month is displayed. `value` supports two-way binding.
```html
<el-calendar v-model="value">
</el-calendar>

<script>
  export default {
    data() {
      return {
        value: new Date()
      }
    }
  }
</script>
```
:::

### Custom Content

:::demo Customize what is displayed in the calendar cell by setting `scoped-slot` named `dateCell`. In `scoped-slot` you can get the date (the date of the current cell), data (including the type, isSelected, day attribute). For details, please refer to the API documentation below.
```html
<el-calendar>
  <!-- Use 3.0 slot syntax. -->
  <template #default="{date, data}">
    <p :class="data.isSelected ? 'is-selected' : ''">
      {{ data.day.split('-').slice(1).join('-') }} {{ data.isSelected ? '✔️' : ''}}
    </p>
  </template>
</el-calendar>
<style>
  .is-selected {
    color: #1989FA;
  }
</style>
```
:::

### Range

:::demo Set the `range` attribute to specify the display range of the calendar. Start time must be Monday, end time must be Sunday, and the time span cannot exceed two months.
```html
<el-calendar :range="['2019-03-04', '2019-03-24']">
</el-calendar>
```
:::

### Attributes
| Attribute       | Description        | Type      | Accepted Values       | Default  |
|-----------------|------------------- |---------- |---------------------- |--------- |
| value / v-model | binding value      | Date/string/number | —            | —        |
| range           | time range, including start time and end time. Start time must be start day of week, end time must be end day of week, the time span cannot exceed two months. | Array  | —  | —  |
| first-day-of-week | fisrt day of week| Number    | 1 to 7                |  1       |

### dateCell scoped slot 参数
| Attribute       | Description   | Type      | Accepted Values       | Default  |
|-----------------|-------------- |---------- |---------------------- |--------- |
| date            | date the cell represents  | Date      | —                     | —        |
| data            | { type, isSelected, day}. `type` indicates which month the date belongs, optional values are prev-month, current-month, next-month; `isSelected` indicates whether the date is selected; `day` is the formatted date in the format yyyy-MM-dd    | Object      | —           | —      |
