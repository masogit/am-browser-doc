# AM Browser configuration

### SSL

After you install AM Browser service and AM REST service, you need to create your server certificate files and overwrite the following certificate files in the ./ssl folder.

- server-cert.pem
- server-key.pem

Then, configure the following sections of the `am-browser-config.properties` file.

### LDAP Authentication

Please reference the AM documentation to configure the LDAP settings in AM:
http://docs.software.hpe.com/AM/9.60/Content/Administration/ch12s07se03.html

> Note: In order to set the certificate file for LDAP over SSL/TLS integration with AM REST server, the configuration file(aamapi96.ini) should be located in following directory:
> C:\Windows\System32\config\systemprofile\AppData\Roaming\HPE\AssetManager\conf\aamapi96.ini

### AM Browser service

The [node] section contains the settings of the AM Browser service, it should resemble the following.

```
[node]
server = 0.0.0.0
port = 8080
https_port = 8443
session_max_age = 30
enable_csrf = true
```

`port` and `https_port` are AM Browser service port. `session_max_age` is AM Browser server session timeout minutes. `enable_csrf` is a toggle for anti-csrf function.

### AM REST service

The [rest] section contains the settings of the AM REST service for AM Browser, it should resemble the following.

```
[rest]
protocol = http
server = localhost 
port = 10081
base = /AssetManagerWebService/rs
version = /v1
```

`server` is AM REST Server address, `port` is AM REST Service port

> You do not need to change `base` and `version`.

### AM Browser Roles

AM Browser has 3 user roles configured in the `am-browser-config.properties` file: Admin, Power User and Guest.

```
[user]
admin = @admin
power = <AM user role1>, <AM user role2>
guest = @anyone
```

`@admin` stands for users who have AM administration rights.  **In this version of AM Browser, AM Browser Admin can only be @admin.**

`@anyone` stands for all AM users including the guest users.

You can assign one or several AM user roles to `power` or `guest`, for example, SAM_Manager, Finance_manager.

### Slack

AM Browser allows you to send message to the channel of `Slack.com`. 

Configure the URL and channel name in the [slack] section so that the Slack function works. 
```
[slack]
#url = https://hooks.slack.com/services/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
channel = #betaprogram

[proxy]
host =
port =
```

### UCMDB
AM Browser has 2 features related to UCMDB, reference Features/Adapter chapter.

- Monitor Adapter
- UCMDB Browser


```
[ucmdb]
adapter = true
browser_server = ucmdbhost
browser_port = 8080
browser_param = /ucmdb-browser/ucmdb_widget.jsp?server=Default%20Client&locale=en#widget=properties;refocus-selection=
```

Setting `adapter` to `false` will disable UCMDB adapter monitor from AM Browser.

> If AM REST Service does not configure the UCMDB connection, Adapter module of AM Browser will not work.

### Environment Parameters
There are some system environment parameters used by AM Browser. The priority is: `Environment Parameters > am-browser-config.properties > am-browser-config.properties.default`

Configure in different systems:

- Unix/Linux - `export AMB_XXX=XXX`
- Windows - `set AMB_XXX=XXX`

Environment Parameters | AM Browser Properties | Comments
---|---|---
NODE_ENV | -- | `production` or `development`
AMB_REST_SERVER | rest.server
AMB_REST_PORT | rest.port
AMB_REST_PROTOCOL | rest.protocol | `http` or `https`
AMB_NODE_SERVER | node.server
AMB_NODE_PORT | node.port
AMB_REST_HTTPS_PORT | node.https_port | `http` or `https`
AMB_SESSION_MAX_AGE | node.session_max_age | (minutes)
AMB_JWT_MAX_AGE | rest.jwt_max_age | (minutes)
AMB_NODE_DEBUG | node.is_debug | `true` or `false`
AMB_NODE_CSRF | node.enable_csrf | `true` or `false`

> Setting `NODE_ENV=production` will significantly improve the performance of the AM Browser Service.
