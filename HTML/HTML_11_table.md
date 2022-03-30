# HTML Table

#### table data &lt;td&gt;

添加表格数据

#### table row &lt;tr&gt;

表格行

#### table head &lt;th&gt;

表头

&lt;col&gt; 元素被规定包含在 &lt;colgroup&gt; 容器中，而 &lt;colgroup&gt;就在 &lt;table&gt; 标签的下方，该方法可以定义整列数据的样式信息

```HTML
<table>
  <colgroup>
    <col>
    <col style="background-color: yellow">
  </colgroup>
  <tr>
    <th>Data 1</th>
    <th>Data 2</th>
  </tr>
  <tr>
    <td>Calcutta</td>
    <td>Orange</td>
  </tr>
  <tr>
    <td>Robots</td>
    <td>Jazz</td>
  </tr>
</table>
````

<table>
  <tr>
    <th>Data 1</th>
    <th style="background-color: yellow">Data 2</th>
  </tr>
  <tr>
    <td>Calcutta</td>
    <td style="background-color: yellow">Orange</td>
  </tr>
  <tr>
    <td>Robots</td>
    <td style="background-color: yellow">Jazz</td>
  </tr>
</table>

如果想把样式信息应用到每一列，我们可以只使用一个 &lt;col&gt; 元素，不过需要包含 span 属性

```HTML
<colgroup>
  <col style="background-color: yellow" span="2">
</colgroup>
```

就像 colspan 和 rowspan, span 需要一个无单位的数字值，用来制定你想要让这个样式应用到表格中多少列

### 为表格添加标题

```HTML
<table>
  <caption>Dinosaurs in the Jurassic period</caption>

  ...
</table>
```

### 添加 `<thead>`, `<tfoot>`, 和 `<tbody>` 结构

- `<thead>` 需要嵌套在 table 元素中，放置在头部的位置，因为它通常代表第一行，第一行中往往都是每列的标题，但是并非每种情况都是这样的。如果使用了 `<col>/<colgroup>` 元素，那么 `<thead>`元素就需要放在它们的下面
 - `<tfoot>` 需要嵌套在 table 元素中，放置在底部 (页脚)的位置，一般是最后一行，往往是对前面所有行的总结
- `<tbody>` 需要嵌套在 table 元素中，放置在 `<thead>`的下面或者是 `<tfoot>` 的下面

### scope属性

#### 定义列标题

```HTML
<thead>
  <tr>
    <th scope="col">Purchase</th>
    <th scope="col">Location</th>
    <th scope="col">Date</th>
    <th scope="col">Evaluation</th>
    <th scope="col">Cost (€)</th>
  </tr>
</thead>
```

#### 定义行标题

```HTML
<tr>
  <th scope="row">Haircut</th>
  <td>Hairdresser</td>
  <td>12/09</td>
  <td>Great idea</td>
  <td>30</td>
</tr>
```

scope 还有两个可选的值 ： colgroup 和 rowgroup。这些用于位于多个列或行的顶部的标题。

### id 和标题属性

如果要替代 scope 属性，可以使用 id 和 headers 属性来创造标题与单元格之间的联系。

1. 为每个`<th>` 元素添加一个唯一的 id 。
2. 为每个 `<td>` 元素添加一个 headers 属性。每个单元格的headers 属性需要包含它从属于的所有标题的id，之间用空格分隔开。

```HTML
<thead>
  <tr>
    <th id="purchase">Purchase</th>
    <th id="location">Location</th>
    <th id="date">Date</th>
    <th id="evaluation">Evaluation</th>
    <th id="cost">Cost (€)</th>
  </tr>
</thead>
<tbody>
<tr>
  <th id="haircut">Haircut</th>
  <td headers="location haircut">Hairdresser</td>
  <td headers="date haircut">12/09</td>
  <td headers="evaluation haircut">Great idea</td>
  <td headers="cost haircut">30</td>
</tr>

  ...

</tbody>
```HTML