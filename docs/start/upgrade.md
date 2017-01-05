### Upgrade/Re-install

HPE updates the installation files once a new version is available. The steps to upgrade/re-install:

1. We recommend that you back up the settings and data although the following files will not be overwritten during upgrade.
    - File <am-browser-rest>\websvc\package.properties
    - File <am-browser>\am-browser-config.properties
    - Folder <am-browser>\db
    - Tomcat <am-browser-rest>\apache-tomcat-8.0.36\conf\server.xml if it is modified.
1. Copy files. Unzip the new package to the correspondent folders to overwrite the old files.

> If you try to deploy REST server war again, make sure that you unregister the previous service and register new service again.

### Migrate file DB to MongoDB

AM Browser 1.1 supports MongoDB to store the configuration data. 