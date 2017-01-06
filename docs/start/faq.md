## AM Browser FAQ

- How does the access control work?

    For the access control of UI functionalities, two groups of users are supported:
    - Admin, those who have the administrator role set in AM (can be found in `Employee and departments`->`Profile` tab -> `Administration rights` ) can access all UI functionalities.
    - Non-admin, can only access `Search`, `Insight` and `Viewer`.
    The data access control permission has the same configuration as `User Rights`, which is based on the operations against each table. (Log on to the AM client as an administrator, menu `Administration`-> `Rights` -> `User rights`)

- Do customers need guest licenses to access AM Browser ?

    No.

- Is Active Directory authentication supported ?

    Yes, AD can be the back-end LDAP server for authentication. However, AM Browser does not support NTLM/IWA authentication currently.

- Can AMB co-exist with AM Web ?

    Yes, AMB is a stand-alone module than AM Web.

- How to restart AMB ?

    - AM REST Service - Run `4_startRestService.bat` to start the service and `5_stopRestService.bat` to stop the service.
    - AM Browser Service - Run `1_startService.bat` to start the service and `2_stopService.bat` to stop the service.
