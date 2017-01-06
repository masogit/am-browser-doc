My Assets module displays out-of-box views to any type of AM users. Before views can be showed, they must be customized by user with admin rights. Admin users set category to My Assets while defining views.  
To normal type user, this module is their default page.

### Default views

In AM Browser 1.1, apart from Summary section, we have provided you four sections of out-of-box views by default:

- PC
- Software
- Organization
- Request

You will easy find assets data related self from this module.

### Summary

Display a dashboard for aggregation data from all views in My Assets module.

![SAM screen shot](img/myassets1.PNG)

### Customization

This module serves as a shortcut representation of group of views, as its data comes from views with user account info as query condition. Each user sees different data from the group views.
To achieve that scenario, you need to follow below rules while defining views.
In addition, in this module, there is no limited number of views can be or which kind of data could be presented.

![SAM screen shot](img/myassets2.PNG)

**Rules**:

- Category name MUST **My Assets**
- Define at least one group by field - aggregation data will display in Summary page
- Define proper AQL conditions

> Ensure each view in My Asset category included these kinds of AQL conditions:

> - User = **currentuser**
> - Portfolio.User.Supervisor = **currentuser**
> - Portfolio.User = **currentuser**
