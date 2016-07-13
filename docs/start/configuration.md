# AM Browser Configuration

After install AM Browser service and REST service (optional), you should configure am-browser-config.properties. (copy properties from am-browser-config.properties.default)

### AM Broser Service

- Both HTTP and HTTPS enabled (For secuirty reason, recommend disable HTTP)
- Overwrite orginazition certificate files in ./ssh folder

### AM REST Service

Specify AM REST Server and port in properties file

```
[rest]
protocol = http
server = localhost
port = 10081
base = /AssetManagerWebService/rs
version = /v1
# 60 minutes
jwt_max_age = 60
```


### User Rights
AM Browser has 3 roles are configured in `am-browser-config.properties` file: Admin, Power user and Guest.

```
[user]
admin = @admin
power = SAM_Manager, Finance_manager
guest = @anyone
```

`@admin` means users have AM administration right.  **Currently, AM Browser's Admin should be configured @admin.**

`@anyone` means users at least have guest licenses.

AM Browser roles | AM profiles
---|---
Admin | @admin
Power user | AM profile1, AM profile2, ...
Guest user | @anyone

Power user and Guest user support to configure AM user profile name. It

> Guest licenses are mininal requirement

### Slack
AM Browser support send message to Slack.com

Confiure url and channel name in properties file, then Slack function works.
```
[slack]
#url = https://hooks.slack.com/services/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
channel = #betaprogram
```

### UCMDB

AM Browser have two features related UCMDB:

- Adpater: Monitor AM Adapters status
- UCMDB Browser: Open specified UCMDB Browser to federate CI info (Need push UCMDB CI with global_id

```
[ucmdb]
adapter = true
browser_server = ucmdbhost
browser_port = 8080
browser_param = /ucmdb-browser/ucmdb_widget.jsp?server=Default%20Client&locale=en#widget=properties;refocus-selection=
```