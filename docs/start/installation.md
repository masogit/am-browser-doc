# AM Browser Installation

### Prerequisite

AM Browser functions on top of Asset Manager 9.5x and 9.60. Before the installation, make sure that your AM Browser server complies with the specifications in AM 9.5x and AM 9.60 support matrices. 

For Asset Manager 9.60 Support Matrix, see [https://softwaresupport.hpe.com/group/softwaresupport/search-result/-/facetsearch/document/KM02417964](https://softwaresupport.hpe.com/group/softwaresupport/search-result/-/facetsearch/document/KM02417964).

For Asset Manager 9.5x Support Matrix, see [https://softwaresupport.hpe.com/group/softwaresupport/search-result/-/facetsearch/document/KM01450310](https://softwaresupport.hpe.com/group/softwaresupport/search-result/-/facetsearch/document/KM01450310).

### Services

AM Browser has the following two services.

- AM Browser Service that provides user interface.
- AM REST Service that provides AM fundamental data service.

### Installation of AM REST Service for the first time

1. Preparation. 

    We recommend that you install AM REST Service on a server that has either AM Windows Client or AM Web Service installed and can connect to AM DB, the configuration of ODBC (64-bit) can be re-used to install the REST Service.

    Otherwise, you need to create an ODBC (64-bit) DSN. To do this, go to the am-browser-rest\bin folder, run `2_registerODBCService.bat` and follow the guide to register SQLSERVER ODBC Data Source Name.


1. Unzip files. 

    Unzip `am-browser-rest-0.1.xxxx.zip` to a folder, for example, am-browser-rest.

1. Configure the server settings. 

    Go to the am-browser-rest\websvc folder, dupilcate the `package.properties.default` file and rename the copy as `package.properties`. In the `package.properties`:

    - DB connection. Make sure the database information such as `DB.datasource`, `DB.login` and `DB.password` is set correctly. Tips: You can refer to AM web service server’s package.properties file as it uses the same settings.
    - UCMDB connection. Make sure `UCMDB.Server.Host`, `UCMDB.Server.Port`, `UCMDB.Server.User` and `UCMDB.Server.Password` are set correctly.
    - Server port. If 10081, the default port of the REST Service, is occupied, modify am-browser-rest\apache-tomcat-8.0.36\conf\server.xml to set another port.

1. (Optional) Generate key files.
    
    - If the server instance is for temporary trial only, you can skip this step and it will use the default files.
    - Generate new key. Go to am-browser-rest\bin folder, run `0_generatePassword.bat` with the Administrator rights.
    - Re-use the existing key files. If there are secret-share files, make sure that the configuration `PBKDF2.Password.First.File` and `PBKDF2.Password.Second.File` in package.properties are set correctly and skip the key file generation.

1. Deploy .war file to Tomcat. 

    Go to the am-browser-rest\bin folder, run `1_deployRestServer.bat` the Administrator rights and follow the instructions.

1. Windows service registration

    - Register: Go to the am-browser-rest\bin folder, run `3_registerRestService.bat` with the Administrator rights, a service named `HPE am-browser-rest-service` is created.
    - Unregister: Go to the bin folder, run `6_unregisterRestService.bat` with the Administrator rights.

1. Start/Stop the REST Service. Run `4_startRestService.bat` to start the service and `5_stopRestService.bat` to stop the service.


### Installation of AM Browser Service for the first time

1. Unzip files. Unzip `am-browser-0.1.xxxx.zip` to a folder, for example, am-browser. 
1. Configure the server settings. Duplicate the `am-browser-config.properties.default` file and rename the copy as `am-browser-config.properties`. In the `am-browser-config.properties` file, make sure the port (`8080` by default) is set correctly and not occupied by other running processes.
1. Windows service registration
    - Register: Run `0_registerService.bat` with Administrator rights, and a service named `HPE am-browser-service` is created.
    - Unregister service. Run `3_unregisterService.bat` with Administrator rights to unregister the service.
1. Start/Stop
    - Start AM Browser Service. Run `1_startService.bat` with Administrator rights to start the service.
    - Stop AM Browser Service. Run `2_stopService.bat` with Administrator rights to stop the service.

### Upgrade/Re-install

HPE updates the installation files once a new version is available. The steps to upgrade/re-install:

1. We recommend that you back up the settings and data although the following files will not be overwritten during upgrade.
    - File <am-browser-rest>\websvc\package.properties
    - File <am-browser>\am-browser-config.properties
    - Folder <am-browser>\db
    - Tomcat <am-browser-rest>\apache-tomcat-8.0.36\conf\server.xml if it is modified.
1. Copy files. Unzip the new package to the correspondent folders to overwrite the old files.