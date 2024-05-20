# **Arcadia Finance Demo App v3**

This repository provides updated version of distributed app demo called "Arcadia Finance".
The app is origal work of Matt from here https://gitlab.com/arcadia-application.

The added feature of this Arcadia Finance v3 are 
**1. Added microservices site name (please refer to red and green circled text on screenshoot below)**
   ![alt text](https://github.com/doddywid/doddywid-demo-app-arcadia-finance-v3/blob/main/arcadia-with-app-site-info.png)
   This information is crucial to demonstrate distributed application, where each of microservices might be served from different sites.
   
**2. Added data reset function**
   ![alt text](https://github.com/doddywid/doddywid-demo-app-arcadia-finance-v3/blob/main/arcadia-reset-all.png)
   Originally, all app data are either stored as json or file in mainapp, app3, and backend containers. After performing several test, a data reset will be required to restore application data state to initial (e.g. account balance, stock portfolio, email referal, transaction history). This reset function also crucial for using traffic generator against the application.
   You can modify reset username and password in /var/www/html/trading/reset_all.php file in "mainapp" container.
   
**3. Dynamic domain and protocol support**
   
   Originally, the domain and protocol for communicating between microservices is hardcoded inside php files. Now, you can set them through environment variables.
   Below are example of running with custom evironment variables
```python
   docker run -dit -h mainapp --restart=always --name=mainapp -e arcadia_appsite="aws2" -e arcadia_proto="https://" -e arcadia_domain="arcadia.example.com" -p 80:80 doddywid/arcadia-mainapp:v3
   docker run -dit -h app2 --restart=always --name=app2 -e arcadia_appsite="aws2" -e arcadia_proto="https://" -e arcadia_domain="arcadia.example.com" -p 81:80 doddywid/arcadia-app2:v3
   docker run -dit -h app3 --restart=always --name=app3 -e arcadia_appsite="aws2" -e arcadia_proto="https://" -e arcadia_domain="arcadia.example.com" -p 82:80 doddywid/arcadia-app3:v3
   docker run -dit -h backend --restart=always --name=backend -e arcadia_appsite="aws2" -e arcadia_proto="https://" -e arcadia_domain="arcadia.example.com" -p 83:80 doddywid/arcadia-backend:v3
```
   Please refer to [docker_run.md](https://github.com/doddywid/doddywid-demo-app-arcadia-finance-v3/blob/main/docker_run.md) for more details on required environment variables.



Docker images are available in public repository of DockerHub as below
| Container Name | Image Name 
|----------------|---------------------------
| mainapp        | doddywid/arcadia-mainapp:v3
| app2           | doddywid/arcadia-app2:v3
| app3           | doddywid/arcadia-app3:v3
| backend        | doddywid/arcadia-backend:v3
