My Assets module presents out-of-the-box views to any type of AM users. Before the views can be presented, they must be customized by user with admin rights. Admin users set category to My Assets while defining views.  
To common users, this module is the default page.

## Default views

In AM Browser 1.1, apart from the Summary section, there are four sections of out-of-the-box views:

- PC
- Software
- Organization
- Request

You can easily find the your asset data with this module.

## Summary

Display a dashboard for the aggregation data from all views in the My Assets module.

![SAM screen shot](img/myassets1.PNG)

## Customization

This module serves as a shortcut of the group of views, its data comes from views and the user account information is used as query condition. Each user sees different data from the group views.
The following rules apply when you define views.
In addition, this module does not limit the number of views or the type of the data to be presented.

![SAM screen shot](img/myassets2.PNG)

**Rules**:

- Category name MUST be **My Assets**
- Define at least one "group by" field - aggregation data will be displayed on the Summary page
- Define proper AQL conditions

> Ensure each view in the My Asset category includs these types of AQL conditions:

> - User = **currentuser**
> - Portfolio.User.Supervisor = **currentuser**
> - Portfolio.User = **currentuser**
