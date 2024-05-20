This repository provides updated version of distributed app demo called "Arcadia Finance".
The app is origal work of Matt from here https://gitlab.com/arcadia-application.

The added feature of this Arcadia Finance v3 are 
1. Added microservices site name (please refer to red and green circled text on screenshoot below)
   ![alt text](https://github.com/doddywid/F5-BIG-IP-to-proxy-AWS-SIGV4-S3-REST-API-with-AWS-Signature-Version-4/blob/main/topology.png)
   This information is crucial to demonstrate distributed application, where each of microservices might be served from different sites.
2. Added data reset.
   Originally, all app data are either stored as json or file in mainapp, app3, and backend microservices. After performing several test, a data reset will be required to restore application data state to initial (e.g. account balance, stock portfolio, email referal, transaction history). This reset function also crucial for using traffic generator against the application.
3. Dynamic domain and protocol support.
   Originally, the domain and protocol for communicating between microservices is hardcoded inside php files. Now, you can set them through environment variables.
