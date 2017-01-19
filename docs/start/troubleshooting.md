
# Troubleshooting

## AM Browser server
In case `http://<node_server_ip>:8888` does not work:

1.	Open a command window and enter `services.msc`, make sure there is an `HPE am-browser-service` service and make sure its status is "Running".
2.	Go to the `<node_server>\log` folder, open `ambrowser.log.YYYY-MM-DD` to check the details.

If you do not see the following messages in the log files, the `HPE am-browser-service` service is not installed correctly and you may try to re-install the service.

```
{"level":"info","message":"[server] Set db folder to ./db","timestamp":"date time"}
{"level":"info","message":"[server] App listening HTTPS on port 8443","timestamp":"date time"}
{"level":"info","message":"[server] App listening HTTP on port 8888","timestamp":"date time"}
```

## AM REST server

If the Node server is started up, but you cannot log on with the correct user name and password, there may be an issue on the REST Server. You can:

1.	Open a command window and enter `services.msc`, make sure there is an `HPE am-browser-rest-service` service and make sure its status is "Running".
2.	Make sure your ODBC connection is created successful. To do this, open `c:\windows\system32\odbcad32.exe` and check the configuration.
3.	Go to `<Rest_Server_DIR>\apache-tomcat-8.0.18\logs` and open `stdout.log` or `stderr.log` for details.

If you still cannot figure out where the problem is, you can pack your Node Log and Rest Log and send them to ambsupport@hpe.com.

## Message

AM Browser displays messages and saves details in `Message History` (Header > User menu > Message History).

Message types are as follows:

- Error
    - User token of AM REST service expired
    - Authentication problems
    - Saved View / Graph / Insight is invalid
    - Retrieving data from AM REST service failed
- Success
    - Creating, updating, deleting data (View / Graph / Insight) successfully
    - Sending message to Slack successfully
- Warning
    - Preview AQL in Graph module, get unexpected data (Column between head and row inconsistent)
- Confirmation
    - Alert confirm window before create, update or delete data
    - Duplicate view or New Graph

> Error, Warning or Success message box will be displayed 5 seconds by default. Click it to close.

## Service Logs
Log file folders

- AM REST Server: <am-browser-rest>\apache-tomcat-8.0.36\logs
- AM Browser Server: <am-browser>\log

## DSN (Data Source Name)
As for DSN setup, refer to AM [installation](installation) guide.

## Login User Name
AM Browser login user name is case sensitive. Different user name will see different Insight dashboard and PDF templates
