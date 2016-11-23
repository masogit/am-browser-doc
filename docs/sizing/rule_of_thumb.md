# Rules of thumb
(All the web related application servers in this section, if not mentioned, are of 64-bit.)
### Asset Manager Browser
Asset Manager Browser is built on a embeded NodeJS server, which provides much higher effiency than any other coponents in Asset Manager.

A standard Asset Manager Browser with 250 ~ 500 concurrent users requires approximately 2GB of RAM.
For CPU utilization, Asset Manager Browser concumes about 40% of Rest Server for the same number of concurrent users. For example: 250 concurrent users.) Therefore, CPU utilization need to be considered if you want to implement Asset Manager Browser on a separate server. 

Concurrent User Count | Estimated Memory Usage
------------------| ------------------ 
250 ~ 500 | 2 GB

<br/>

### Asset Manager Rest Server


Current version of Rest Server is mostly based on Asset Manager Web Service, except below changes:

* Rest Server is only capable of serving Restful requests in production environment.
* Rest Server does not load web service tags so it will take much less time during startup.


There are several `major checkpoints` before go to production:

* Memory:
*Best practice configurations has been already configured during service installation, you only need to increase the value if required.*

Concurrent User Count | Estimated Memory Usage
------------------| ------------------ 
250  | 4 GB (1.75 GB for JVM, 700~900 MB for overhead and cache, 5~10 MB per connection.)

* Connection pool configurations (aamapi.ini):

Concurrent User Count | CnxPoolIdleSize | CnxPoolMaxSize
------------------| ------------------ | ------------------ 
250  | CnxPoolMaxSize - 5 | 500 or higher

For other details on Asset Manager Web Service Server, please refer to [Asset Manager 9.60 Deployment Sizing Guide](https://softwaresupport.hpe.com/group/softwaresupport/search-result/-/facetsearch/document/KM02559120)