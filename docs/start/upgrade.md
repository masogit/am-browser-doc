## Upgrade/Re-install

HPE updates the installation files once a new version is available. The steps to upgrade/re-install:

1. We recommend that you back up the settings and data although the following files will not be overwritten during upgrade.
    - File <am-browser-rest>\websvc\package.properties
    - File <am-browser>\am-browser-config.properties
    - Folder <am-browser>\db
    - Tomcat <am-browser-rest>\apache-tomcat-8.0.36\conf\server.xml if it is modified.
1. Unzip the new package, copy the files mentioned in step 1 to overwrite the old ones .

> If you try to deploy REST server (the .war file) again, make sure you unregister the previous service and register new service again.

## Migrate file DB to MongoDB

AM Browser 1.1 supports both file DB and MongoDB to store the configuration data. It also supports migrating data from file DB to MongoDB.

Make sure to correctly configure the connection parameter for both file DB folder and MongoDB, refer to section [Configuration](configuration/#database-configuration) for more information. Run the following script with administrator or root rights:

- `db_migrate.bat` in window package
- `db_migrate.sh` in linux package

*The lines from command*
```
info: [Migrating] Migrating from file to mongodb
info: [Migrating] Loading data from folder: ./db
info: [Migrating] Exporting collection: report, records: 1
info: [Migrating] Exporting collection: wall, records: 3
info: [Migrating] Exporting collection: view, records: 12
info: [Migrating] Exporting collection: aql, records: 26
info: [Migrating] Connecting mongodb: mongodb://localhost:27017/amb
info: [Migrating] Mongodb localhost connected
info: [Migrating] 42 record(s) already be imported successfully.
```

> MongoDB migrating to file DB is not supported.
