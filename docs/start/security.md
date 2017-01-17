This section is intended for system engineers and administrators who need to securely implement the AM Browser in their environment.

## Secure Implementation and Deployment

### Technical System Landscape
AM Browser is a suite of enterprise applications based on various industry standard technologies. For details about the architecture of AM Browser, refer to the AM Browser installation section of this document.

### Security in Basic and Clustered AM Browser Configurations
Web browser is the only client side in AM Browser, users can be authenticated via the following authentication methods:
* Login/Password authentication
* LDAP authentication
The Web client’s three-tier structure can spread over multiple hosts; the data transferred over the network can be configured to use the HTTPS protocol.
* The browser exchanges data with the AM Browser server using HTTP/HTTPS protocol.
* The AM Browser server communicates with the AM REST server also using HTTP/HTTPS protocol.

### Proxy Authentication Support
AM Browser supports the use of proxy servers that require authentication. AM Browser can run in a number of distinct implementations. If there is a security requirement to separate the end user’s browsers from the AM Browser via a proxy device that requires authentication, this is supported transparently as the authenticated proxy configuration is specified in the user’s web browser settings. For information about how to configure a proxy server for your browser, refer to the following:
* Microsoft Internet Explorer
  http://support2.microsoft.com/kb/135982
* Mozilla Firefox
  https://support.mozilla.org/en-US/kb/advanced-settings-browsing-network-updates-encryption#w_connection
* Google Chrome
  https://support.google.com/chrome/answer/96815


##	Network and Communication Security
This section provides information about network and communication security.
### Secure Topology
AM Browser is designed to be part of a secure architecture, and can meet the challenge of dealing with the security threats to which it could potentially be exposed.
Several measures are recommended to securely deploy AM Browser:
*	Use of the TLS/SSL communication protocol
The SSL protocol secures the connection between two communication end-points, typically the client and the server. URLs that require a secure connection to start with HTTPS instead of HTTP. Enable TLS/SSL communications between:
  * The browsers and the AM Browser server
  * The AM Browser server and AM REST server
  * AM REST server and optional Directory Services Server (LDAP server)
  * AM REST server and third-party Web Services integrations

* Reverse proxy architecture
AM Browser supports reverse proxy architecture as well as secure reverse proxy architecture. Reverse and secure reverse proxy server environments are typically implemented in support of the AM Browser component. That is, browsers that need access to AM Browser will do so via the reverse or secure reverse proxy server. In addition, hardware load balancing devices such as F5 provide equivalent reverse and secure reverse proxy server capabilities when managing traffic between the AM Browser component and the AM REST server component.
For information about load balancing, see the HPE Asset Manager Online Help Center topic, High Availability Guidelines.
* DMZ architecture using a firewall
The basic concept is to create a complete separation, and to avoid direct access, between the web browser and the AM Browser servers. This is especially important when opening access to AM Browser to external clients from outside of your organization.
* Separation between web servers, application servers, load balancers, and database servers 

### Reverse Proxy Overview
A reverse proxy is an intermediate server that is positioned between the client machine and the web servers. To the client machine, the reverse proxy seems like a standard web server that serves the client machine’s HTTP or HTTPS protocol requests, with no dedicated client configuration required.

The client machine sends ordinary requests for web content, using the name of the reverse proxy instead of the name of a web server. The reverse proxy then sends the request to one of the web servers. Although the response is sent back to the client machine by the web server through the reverse proxy, it appears to the client machine as if it is being sent by the reverse proxy.

### Reverse Proxy Security
A reverse proxy functions as a bastion host. It is configured as the only machine to be addressed directly by external clients, and thus obscures the rest of the internal network. Use of a reverse proxy enables the application server to be placed on a separate machine in the internal network, which is a significant security objective.

DMZ is a network architecture in which an additional network is implemented, enabling you to isolate the internal network from the external one. Although there are a few common implementations of DMZs, this section discusses the use of a DMZ and reverse proxy in a back-to-back topology environment.

The following are the main security advantages of using a reverse proxy in such an environment:
*	No DMZ protocol translation occurs. The incoming protocol and outgoing protocol are identical (only a header change occurs).
*	Only HTTP or HTTPS access to the reverse proxy is allowed, which means that stateful packet inspection firewalls can better protect the communication.
*	A static, restricted set of redirect requests can be defined on the reverse proxy.
*	Most of the web server security features are available on the reverse proxy (authentication methods, encryption, and more).
*	The reverse proxy screens the IP addresses of the real servers as well as the architecture of the internal network.
*	The only accessible client of the web server is the reverse proxy.
*	This configuration supports NAT firewalls.
*	The reverse proxy requires a minimal number of open ports in the firewall.
*	The reverse proxy provides good performance compared to other bastion solutions.
*	Using a secure reverse proxy architecture is easier to maintain. You can add patches to your reverse proxy as needed
 
Note:
*	It is expected and recommended that the front end server (load balancer or reverse proxy) will be configured to require TLS/SSL.
*	Follow security guidelines for third-party LDAP servers and Oracle or SQL databases.


## User Management and Authentication
This section provides information related to user management and authentication.

### Authentication Model
Asset Manager supports the following authentication methods:
*	Username and password authentication
  
  In an out-of-the-box default installation, AM Browser requires users to enter username and password credentials to gain access to the application. This basic authentication and authorization provider for AM Browser consists of a non-FIPS 140-2 compliant module that utilizes industry standard cryptography such as AES CBC and Triple-DES CBC.
*	LDAP authentication
  
  You can integrate AM Browser to an LDAP directory service to share contact information across your network.


## Authorization
This section provides information related to user authorization in AM Browser.
### Authorization Model
Access to AM Browser resources is authorized based on the user’s following settings: 
*	User role
*	User rights
*	Profile
*	Functional rights
*	Access restriction 
*	License
*	Session & Inactivity timer timeouts
*	Password expiration policy
For full detail on the authorization model of AM Browser, please refer to the AM Browser Administration in the installation media.
### Authorization Configuration
For detailed information on authorization configuration, please refer to the HPE Asset Manager Administration in the installation media.

## Data Integrity
Data integrity is a critical security requirement. The data backup procedure is an integral part of this requirement. AM Browser does not provide backup capabilities. Following are some important considerations:
*	Database backup is especially important before critical actions such as upgrades. See the AM migration document in the installation media for details.
*	Backup files should be stored properly according to the industry best practices to avoid unauthorized access.
*	Since database backup can be a resource intensive process, it is strongly recommended to avoid running backups during peak demand times.
For more details, refer to the AM High Availability Guidelines in the installation media.

## Encryption
This chapter provides information on data encryption in AM Browser.

###TLS/SSL Data Transmission

In production environments, AM Browser must be configured to use TLS/SSL to transmit data between the server and clients, as well as between the web application server and web browser so that data being transmitted is encrypted. 
For detail TLS/SSL configurations, please reference HPE Asset Manager Web Implementation in the installation media.

### Encryption of stored database fields

AM Browser REST server uses proprietary algorithms when encrypting data stored in the database. For example, passwords for operators are stored using SHA-256 a one-way encryption algorithm. In production environments that require stronger encryption algorithms, AM Browser REST server offers FIPS 140-2 compliant encryption modules for enhanced security. Details about FIPS 140-2 configuration can be found in the HP Asset Manager Installation and Upgrade from installation media.

### Digital Signatures
HPE digitally signs Windows binaries such as libaamapi96.dll and using Microsoft Authenticode technology. To view the details of the digital signature, right-click on the Windows binaries, select Properties, and click the Digital Signatures tab. Select the ‘Hewlett Packard Enterprise Company’ signature and click the Details button. Windows will verify if the digital signature is valid or not.
In cases where your Windows operating system may not have the latest CA Root Certificates installed, the digital signature of the HPE Windows binaries (libaamapi96.dll and/or other binaries) may display an error such as:
“The certificate in the signature cannot be verified.”

To resolve this issue, either enable Windows Update to download the latest updates available for your operating system or download and install the G5 Root certificate as documented here:
https://knowledge.verisign.com/support/ssl-certificates-support/index?page=content&id=SO19140



