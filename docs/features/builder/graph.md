# AM Browser Graph

The Graph module provides data query, statistics and visual graph features. Admin users can input AQL (Asset Manager Query Language) to query data, for those aggregation data, it is easy to configure a Graph for presenting.

### Graph styles and designer
Currently, there are 3 types of Graph with designer. These graphs are built with original Grommet components, each Grommet component has several sub types:

- Chart: Bar, Line, Area
- Meter: Bar, Arc, Circle, Spiral
- Distribution

> Only aggregation AQL query data can be configured in Graph designer.

### AQL data and configuration

Admin user inputs aggregation AQL, like: `select seBasis, count(*) from amNature group by seBasis`

- Preview
- Configure Graph form
- Attached view

#### Preview

After you input aggregation AQL, you can use Preview to get a query result. It should have some columns.

> It is suggested to have the first column as the group by field and the second column as `count(*)` or `sum(<field name>)`.

> Some AQL functions can not work currently.

<table>
    <tr>
         <th colspan='5' width=20%>for example:</th>
    </tr>
    <tr>
        <td>IsNull</td>
        <td>NullBlob()</td>
        <td>NullMemo()</td>
        <td>NullString()</td>
        <td>NullDate()</td>
    </tr>
    <tr>
        <td>NullTime()</td>
        <td>Trunc()</td>
        <td>NullTimeStamp()</td>
        <td>NumberToTime()</td>
        <td>TextToTime()</td>
    </tr>
    <tr>
        <td>DataLength()</td>
        <td>Ceil()</td>
        <td>Floor()</td>
    </tr>
</table>

#### Configure Graph designer

After getting a query result table with some columns,  you can create a graph from Graph designer. Specify **Column** of Graph designer from one of columns in the query result table.

##### Basic properties
- **Column** (mandatory)
> When you input  aggregation AQL, it should display some columns.**Column** will create some selectable buttons by pure numeric columns. You can select a button, it will display a graph. If you have more than one selectable button. You can do multiple choice in Chart, it will display a composite graph. But you only  do single choice in Meter and Distribution.

- Label
    - X Axis label in Chart
    - Column units in Meter
    - Label in Distribution
- Other properties
    - Type
    - Size
    - X Axis placement in Chart

##### Advance properties
-  Legend properties
    - Legend position
    - Legend units
    - Legend total
-  Details(in Chart and Meter) properties
    - Important
    - Threshold
    - Max
    - Min
- Other properties
    - Points in Chart
    - Stacked in Meter
    - Vertical in Meter

![Graph](../img/graph3.png)

#### Attached View

Attach a graph with a View, then you can click an element. A page will pop up and show records list as filtered result. You should  input Field and select Value to configure the filter.
>IF you input  aggregation AQL, it will display some columns, **Value** is one of the columns.

>**Field** is one of the columns in the View.

- Field and Value is null. When you click an element, it will query the complete set of data in the View.
- Field and Value is not null. It means you put the **Value** values as a condition to the Field, will query with this condition in the VIEW .And return a subset of View.


### Example
If you want to create a Graph like this :
>![Graph](../img/graph4.PNG)
> 1.You click New Tab to create a new Graph.

> 2.You should input the Name and aggregation AQL in the right textarea, then it will display a records list.

>3.You should input Category to define the main menu item in the left bar.

>4.Now,you click a  selectable button in Column, it will display a graph(if not have selectable button, please check out your aggregation AQL). You can choose some properties to change the details about graph.

>5.You can Query, Save, Delete, Mail and Download your graph by click these buttons.

If you want to click the element of Graph to get a records list view. You should click Attached View, select a existing View and configure Field
and Value.
