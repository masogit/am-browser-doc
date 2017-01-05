# Introduction
This sizing section provides recommendations for the deployment of Asset Manager Browser to avoid big architecture level performance issues, thus achieving `go to production`. 
Information about performance is derived from tests performed on released versions only and is therefore intended for reference only. 
Guides for other components of Asset Manager can be found at the following HPE website:

>[http://softwaresupport.hpe.com/](http://softwaresupport.hpe.com/).

The reference configuration data supplied in this document is based on an Asset Manager out-of-box (OOB) environment, which includes the Asset Manager Browser and Restful server.
Individual implementations may consume more resources or require more resources to perform in an acceptable manner. This includes running an implementation on top of tailored version of Asset Manager.
Before going online, a performance test simulating the concurrent user load and transaction rate of actual daily system usage for the tailored application in a test environment is highly recommended. Ignoring this step may result in an environment that is not large enough to support your requirements.
The recommendations described in this section should be considered the minimum requirements that are needed to run Asset Manager Browser effectively.

**Table of Contents**

- [Sizing Questions](sizing_questions)
- [Deployment Modes and Sizing](sizing/deployment_modes_and_sizing)
- [Rules of thumb](sizing/rule_of_thumb)
- [Appendix A - Asset Manager Browser benchmark performance test results](sizing/appendix_a)
- [Appendix B - Asset Manager Browser processing capability test results](sizing/appendix_b)
- [Appendix C - Asset Manager Browser sample deployment configuration and tuning for benchmark](sizing/appendix_c)
- [Appendix D - Database volume size of sample deployment](sizing/appendix_d)
- [Appendix E - Links](sizing/appendix_e)