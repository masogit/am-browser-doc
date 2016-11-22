# Introduction
This guide provides recommendation and suggestion on Asset Manager Browser to help you easily `go to production` without big architecture level performance issue. 
Information on performance is derived from tests performed on released versions only and is therefore intended for reference only. 
Guides for other components of Asset Manager can be found at the following HPE website:

>[http://softwaresupport.hpe.com/](http://softwaresupport.hpe.com/).

The reference configuration data supplied in this document is based on an Asset Manager out-of-box (OOB) environment, which includes the Asset Manager Browser and Restful server.
Individual implementations may consume more resources or require more resources to perform in an acceptable manner. This includes running an implementation on top of tailored version of Asset Manager.
Before going online, a performance test simulating the concurrent user load and transaction rate of actual daily system usage for the tailored application in a test environment is highly recommended. Ignoring this step may result in an environment that is not large enough to support your requirements.
The recommendations described in this document should be considered the minimum requirements that are needed to run Asset Manager effectively.
