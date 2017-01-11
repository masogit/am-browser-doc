# AM Browser View Builder

AMB View is a lightweight component that presents AM data, Admin users may create and manage views in AMB Builder. Power users can query all views in AMB Viewer. Guests can access a view a URL that is shared by Admin users.

A view is created from AM schema (raw table), and a view only has one root table. All fields or links are related to the root table.  

## Fields and Links
Fields and links are selected from AMB Build Schema. When a root table is selected, it cannot be changed. Fields and links are split into 3 groups:

- 1-M Links
- 1-1 Links
- Fields

All fields or 1-1 link's fields will be added in the same link. When data is being queried from this view, these fields are queried and displayed together. For example:

```
Root table:
        amComputer
Fields:
        CPUType
        Portfolio.seAssignment
        Portfolio.Model.Name
        Portfolio.Brand.Name
```

When fields in 1-M Links are selected, a new link is created. For example:

```
1-M link:
        PhysicalDrivers
Field:
        lTotalSizeMb
```
```
1-M link:
        Portfolio.Softs
Field:
        Folder
        Model.Name
        Model.Brand.Name
```

## Functions

The following functions take effect in each link (Root or 1-M link).

- Searchable
    - Only 2 fields in a link can be set to "searchable".
    - Press Enter in the viewer search box, it will generate AQL filters to query data on this field.
    - The searchable fields of the root table can be searched in Global Search.

- Group by
    - Set the default group by field, it will show group by graph when querying in viewer.
- Sum
    - If a field has group by, it allows you to select a number field to sum.
- Order by
    - Set a field as order by field.
- Set alias
    - Set Alias name to replace the label displayed in the viewer.
- Filter
    - Specify AQL filter condition when querying data. Example: `Name like '%ABC%' or AssetTag like'123ABC%'`
- Sort fields
    - Adjust display order of fields.

## Others

- Click each link title, AM schema side bar will address the table directly.
- Export view definition as json file.
- Share a view with guest users by sending a URL in email.

> Define **My** view with `CurrentUser` in AQL filter, e.g.: `Portfolio.User=CurrentUser`, then share it to guest users. They can query their own AM data.
