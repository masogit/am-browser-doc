# AM Browser installation

## Prerequisite

AM Browser functions on top of Asset Manager 9.5x and 9.60. Before the installation, make sure that your AM Browser server complies with the specifications in AM 9.5x and AM 9.60 support matrices.

For Asset Manager 9.60 Support Matrix, see [https://softwaresupport.hpe.com/group/softwaresupport/search-result/-/facetsearch/document/KM02417964](https://softwaresupport.hpe.com/group/softwaresupport/search-result/-/facetsearch/document/KM02417964).

For Asset Manager 9.5x Support Matrix, see [https://softwaresupport.hpe.com/group/softwaresupport/search-result/-/facetsearch/document/KM01450310](https://softwaresupport.hpe.com/group/softwaresupport/search-result/-/facetsearch/document/KM01450310).

> AM Browser packages are self-contained. It does not require any other AM components during installation. What you need is only the AM database and a well configured database connection that can be used by AM.

## Services

AM Browser has the following two services.

- AM Browser Service that provides user interface.
- AM REST Service that provides AM fundamental data service.

> Make sure you always use the REST Service shipped with AM Browser to get the best compatibility.

## Deployment

It is recommended that AM Browser connects to a **Standby RDBMS**.

![Deploy diagram](img/AMB_1.0_Standalone.png)


## Install AM REST Service for the first time

> **If your OS is `Windows Server 2008 R2`, please run the `.bat` or `.cmd` files in command line to make sure they can be executed properly.** 

1. Preparation.

    We recommend that you install AM REST Service on a server that has either AM Windows Client or AM Web Service installed and can connect to the AM database, the configuration of ODBC (64-bit) can be reused to install the REST Service.

    Otherwise, you need to create an ODBC (64-bit) DSN. To do this, go to the `am-browser-rest\bin` folder, run `2_registerODBCService.bat` and follow the guide to register SQLSERVER ODBC Data Source Name.


1. Unzip files.

    Unzip `am-browser-rest-1.0.zip` to a folder, for example, am-browser-rest.

1. Configure the server settings.

    Go to the am-browser-rest\websvc folder, duplicate the `package.properties.default` file and rename the copy as `package.properties`. In the `package.properties`:

    - DB connection. Make sure the database information such as `DB.datasource`, `DB.login` and `DB.password` is set correctly. Tip: You can refer to AM web service server’s package.properties file as it uses the same settings.
    - UCMDB connection. Make sure `PushAdapter.Monitor.Enabled`, `UCMDB.Server.Host`, `UCMDB.Server.Port`, `UCMDB.Server.User` and `UCMDB.Server.Password` are set correctly.
    - Server port. If 10081, the default port of the REST Service, is occupied, modify am-browser-rest\apache-tomcat-<version>\conf\server.xml to set another port.

1. Generate key files.

    - If the server instance is for temporary trial only, you can skip this step and it will use the default files.
    - Generate a new key. Go to am-browser-rest\bin folder, run `0_generatePassword.bat` with the administrator right.
    - Reuse the existing key files. If there are secret-share files, make sure the parameter `PBKDF2.Password.First.File` and `PBKDF2.Password.Second.File` in package.properties are set correctly and skip the key file generation.

1. Deploy the .war file to Tomcat.

    Go to the am-browser-rest\bin folder, run `1_deployRestServer.bat` with the administrator right and follow the instructions.

1. Windows service registration

    - Register: Go to the am-browser-rest\bin folder, run `3_registerRestService.bat` with the administrator right, a service named `HPE am-browser-rest-service` is created.
    - Unregister: Go to the bin folder, run `6_unregisterRestService.bat` with the administrator right.

1. Start/Stop the REST Service.

    Run `4_startRestService.bat` to start the service and `5_stopRestService.bat` to stop the service.


## Install AM Browser Service for the first time

1. Unzip files. Unzip `am-browser-1.0.zip` to a folder, for example, am-browser.
1. Configure the server settings. Duplicate the `am-browser-config.properties.default` file and rename the copy as `am-browser-config.properties`.
In the `am-browser-config.properties` file, make sure the port (`8080` by default) is set correctly and not occupied by other running processes.
Please refer to [Configuration Chapter](configuration) for details.

1. Windows service registration
    - Register: Run `0_registerService.bat` with the administrator right, and a service named `HPE am-browser-service` is created.
    - Unregister service. Run `3_unregisterService.bat` with the administrator right to unregister the service.
1. Start/Stop
    - Start AM Browser Service. Run `1_startService.bat` with the administrator right to start the service.
    - Stop AM Browser Service. Run `2_stopService.bat` with the administrator right to stop the service.
