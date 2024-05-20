Example of docker run command 
```python
   docker run -dit -h mainapp --restart=always --name=mainapp -e arcadia_appsite="aws2" -e arcadia_proto="https://" -e arcadia_domain="arcadia.example.com" -p 80:80 doddywid/arcadia-mainapp:v3
   docker run -dit -h app2 --restart=always --name=app2 -e arcadia_appsite="aws2" -e arcadia_proto="https://" -e arcadia_domain="arcadia.example.com" -p 81:80 doddywid/arcadia-app2:v3
   docker run -dit -h app3 --restart=always --name=app3 -e arcadia_appsite="aws2" -e arcadia_proto="https://" -e arcadia_domain="arcadia.example.com" -p 82:80 doddywid/arcadia-app3:v3
   docker run -dit -h backend --restart=always --name=backend -e arcadia_appsite="aws2" -e arcadia_proto="https://" -e arcadia_domain="arcadia.example.com" -p 83:80 doddywid/arcadia-backend:v3
```

The command follows ordinary docker command structure.
The required environment variables are
|  No  | Environment Variable Name | Sample Value        | Description                                                                                                   |
|------|------------:--------------|---------------------|---------------------------------------------------------------------------------------------------------------|
|  1   | arcadia_appsite           | aws2                | Site name on where the particular microservices is deployed.                                                  |
|  2   | arcadia_domain            | arcadia.example.com | The domain name, used by containers to comunicate to other microservices.                                     |
|  3   | arcadia_proto             | https://            | The protocol, can be either "https://" or "http://", used by containers to comunicate to other microservices. |

