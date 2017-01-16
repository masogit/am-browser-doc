
Software Asset Management is an important feature of Asset Manager.
In AM Browser you will find a simplified module that displays the SAM status dashboard. As show in the following sequence:

>  *Effective License Positioning (Vendor)* > *Product* > *Version* > *Computer*

## Effective License Positioning

- All software vendors are listed in cards.
- Sorting by **Non-Compliance** or **Over-Compliance** is supported (**Non-Compliance** by default).
- Sorted items are colored in cards.
- You can click the card to switch to the product page.

>   *To note:  if the value of sorting items is zero, we ignore painting them.*


![SAM screen shot](img/sam1.png)

## Product

- All products of a vendor are listed in cards.
- Sorting by **Non-Compliance** or **Over-Compliance** is supported (**Non-Compliance** by default).
- Sorted items are colored in cards.
- You can click the card to switch to the version page.

![SAM screen shot](img/sam2.png)

## Version

- All versions of a product are displayed in table mode.
- You can click a record to review the computers where this version of the software is installed.

![SAM screen shot](img/sam3.png)

## Computer

- All computers where the particular version of software is installed are listed.
- Computer records are displayed in a pop-up window.
- Records are "grouped by" hardware type by default.

![SAM screen shot](img/sam4.png)

>  Computers are not listed if the particular software is not installed on them.

## Usability

- **Breadcrumb**

  On the top of page, there is a special breadcrumb, each entry of which is a dropdown menu instead of a simple link.  
  By using the menu, AM Browser allows you to navigate to the last level of the vendor or switch among products easily.  
  For instance, you are scanning AssetManager product purchased from vendor HP:

  ![SAM screenshot - breadcrumb](img/sam5.png)

  You can switch to other vendors of yours, for example, "*HP Discovery and Dependency Mapping Inventory*" or "*HP Network Node Manager i*."  
  Moreover, you can change vendor at this level by simply selecting one from the vendor drop down menu.

- **Sort Menu**

  A sort menu is added on each card page, allowing you to sort vendors or products with some of their attributes.  
  With this feature, you can sort them with the value of that contained attribute and emphasize them.  
  By default, vendors are sorted with the attribute of **Non-Compliance** and products with **Gap**.

- **Search**

  Next to the sort menu, a search input is implemented enabling you to perfrom quick search for vendors or products.
