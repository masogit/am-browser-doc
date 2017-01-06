My It Assets module is some out-of-box views for any AM users, it can be customized by administrator. 
This module is the default page for Normal User.

### Default views

In AM Browser 1.1, there are four out-of-box views:

- PC
- Software
- Organization
- Request

Users will easy find assets data related self from this module.

### Summary

Display a dashboard for aggregation data from all views in My Assets module.

![SAM screen shot](img/myassets1.PNG)

### Customization

This module designed for a shortcut views category to query user related data, and there is no limitation to how many views or what's kind of data should present.

![SAM screen shot](img/myassets2.PNG)

**Rules**:

- Category name MUST **My Assets**
- Define at least one group by field - aggregation data will display in Summary page
- Define proper AQL conditions

> Ensure each view in My Asset category included these kinds of AQL conditions:

> - User = **currentuser**
> - Portfolio.User.Supervisor = **currentuser**
> - Portfolio.User = **currentuser**