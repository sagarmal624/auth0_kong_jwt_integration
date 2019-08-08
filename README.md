# Auth0 Integration with Kong-JWT Plugin
[![Build Status](https://travis-ci.org/joemccann/dillinger.svg?branch=master)](https://travis-ci.org/joemccann/dillinger)

# Installation Steps

## Step-1 : Add JWT Plugin for Services/Routes
![alt text](https://raw.githubusercontent.com/sagarmal624/auth0_kong_jwt_integration/master/1.png)
## Step-2 : Download your Auth0 account's Certificate with below url
```bash
  https://<COMPANY-NAME>.auth0.com/pem
```
## Step-3: Transform the Certificate into a public key with below command
```bash
openssl x509 -pubkey -noout -in <COMPANY-NAME> > pubkey.pem
```
## Step-4: Create a Consumer
![alt text](https://raw.githubusercontent.com/sagarmal624/auth0_kong_jwt_integration/master/2.png)
## Step-5: Update a consumer with the Auth0 public key 
```bash
curl -i -X POST http://192.168.99.100:9001/consumers/user123/jwt \
    -F "algorithm=RS256" \
    -F "rsa_public_key=@./pubkey.pem" \
    -F "key=https://<COMPANY-NAME>.auth0.com/"

```
## Step-6: Now Access your Service
![alt text](https://raw.githubusercontent.com/sagarmal624/auth0_kong_jwt_integration/master/4.PNG)
![alt text](https://raw.githubusercontent.com/sagarmal624/auth0_kong_jwt_integration/master/3.png)


