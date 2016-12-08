# Appendix D: Database volume size of sample deployment 
#### Database volume size
The following table shows the disk usage of data sets on Oracle database.

- All the databases use the default character set. Converting to UTF may add more disk usage. 
- Disk usage may vary as per the usage on various set of customer data.
- Disk usage for supporting usage, such as temporary space and database system level disk usage, are not included.

    | Database Type                                     | Data Set                                                         | Disk Usage       |
    |---------------------------------------------------|------------------------------------------------------------------|------------------|
    | Oracle 11g2                                       | Simulated data set, check below table for details                | 8.2 GB           |

- Detailed data information (tables with more than 200K rows are listed)

    | Table Name      | Size   | Record Count |
    |-----------------|--------|--------------|
    | AMHISTORY       | 870 MB | 10M rows     |
    | AMSOFTINSTALL   | 174 MB | 1M rows      |
    | AMCOMMENT       | 993 MB | 800K rows    |
    | AMASSET         | 378 MB | 700K rows    |
    | AMPORTFOLIO     | 198 MB | 700K rows    |
    | AMCLEASEDETAIL  | 194 MB | 700K rows    |
    | AMCOMPUTER      | 181 MB | 600K rows    |
    | AMCLEASEDTLDESC | 39  MB | 600K rows    |
    | AMPORDLINE      | 138 MB | 500K rows    |
    | AMEMPLDEPT      | 142 MB | 400K rows    |
    | AMASTCNTRDESC   | 13  MB | 300K rows    |
    | AMWFINSTANCE    | 21  MB | 300K rows    |
    | AMINVENTMODEL   | 37  MB | 200K rows    |
    | AMPORDER        | 53  MB | 200K rows    |
