# Sizing Questions
The following list of questions is designed to gather the information that is required to make recommendations about the overall system architecture that you need for your Asset Manager Browser environment.   

>Note: Although not all of the information requested here is required to size the environment, it is useful information to obtain for a thorough architecture recommendation. 

1.	What kind of environment will be used?
	1.	An on-premise solution administered by internal IT
	2.	An in-house solution administered by HPE
	3.	Software as a service
2.	What is the expected hardware and software environment?
	1.	Do you plan to operate in separate development, test, and production environments to ensure quality?
	2.	Do you have any disaster recovery, or high availability requirements?
	3.	Do you plan to operate in a virtual environment or on physical machines?
3.	Is there any existing hardware to be reused?
	1.	What operating systems are you using? Are these 32-bit or 64-bit operating systems?
	2.	How many CPUs are there per machine?
	3.	How much RAM is available per machine?
	4.	What relational database management system is used currently?
	5.	If the answer to 4 is yes, is it a cluster environment?
4.	Can you provide a Microsoft Visio diagram of your network with minimum latency and bandwidth values?
5.	Do you plan to use any of the following integrations together with Asset Manager?  If so, which ones?
	1.	Messaging system: SMTP, MAPI or SMTP
	2.	Active Directory (LDAP) integration or single sign-on
	3.	Data import of persons or organizations from an HR or other environment
	4.	Integration to Universal Configuration Management Database (UCMDB)/CMS
	5.	Integration to other HPE Software solutions
	6.	Imported configuration items (CIs)
	7.	Others
6.	Do you have requirements for any of the following components and modules?
	1.	Additional languages. If yes, which languages do you expect to operate?
	2.	IT specialists (Technicians, Administrators). If yes, what is the overall number of IT specialists? (Technicians, Administrators)
	3.	Named/Floating Users. If yes, how many of them should have guaranteed access to Asset Manager?
	4.	What are your module-level user requirements for Asset Manager?
7.	How many users will have access to Asset Manager Web Tier/ Asset Manager Browser?
8.	What is the geographical breakdown of your web user base in workday bandwidth (7x24)?
9.	What is the concurrent users of Asset Manager Web Tier / windows client / Asset Manager Browser?
10.	What is the concurrent user number of Asset Manager based on each module?
11.	What are your expected data volumes (including attachments) for the following modules?
	1.	Cable and Circuit
	2.	Contracts
	3.	Financials
	4.	Portfolio
	5.	Procurement
	6.	Reconciliation Proposal
	7.	Software Assets
12.	What are your expected increasing speed of data volumes for the above modules? (e.g.: 50 procurement requests per day / 300 software installations per day )
13.	Will you keep history in Asset Manager? (In Asset Manager, the history of changes made to the fields and links of a table can be tracked and recorded.)
14.	What are your reporting requirements?
	1.	The bundled Crystal Reports solution
	2.	In-tool reporting
	3.	An external reporting solution
	4.	Data replication into a data warehouse
15.	Which browser are you using?
16.	Do you use Citrix in your network?


> Note: Use the calculation in the "Rules of thumb" section to estimate the ratio of Self Service users to concurrent users. 

