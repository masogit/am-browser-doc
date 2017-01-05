# Introduction
This sizing section provides recommendations for the deployment of Asset Manager Browser to avoid big architecture level performance issues, thus achieving `go to production`. 
Information about performance is derived from tests performed on released versions only and is therefore intended for reference only. 
Guides for other components of Asset Manager can be found at the following HPE website:

>[http://softwaresupport.hpe.com/](http://softwaresupport.hpe.com/).

The reference configuration data supplied in this document is based on an Asset Manager out-of-box (OOB) environment, which includes the Asset Manager Browser and Restful server.
Individual implementations may consume more resources or require more resources to perform in an acceptable manner. This includes running an implementation on top of tailored version of Asset Manager.
Before going online, a performance test simulating the concurrent user load and transaction rate of actual daily system usage for the tailored application in a test environment is highly recommended. Ignoring this step may result in an environment that is not large enough to support your requirements.
The recommendations described in this section should be considered the minimum requirements that are needed to run Asset Manager Browser effectively.
