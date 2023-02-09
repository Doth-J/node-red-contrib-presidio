# node-red-contrib-presidio :package: 

This is a subflow for interacting with the Microsoft Presidio Analyzer and Anonymizer services.

## Install :zap:

Run the following command in your Node-RED user directory - typically `~/.node-red`

        npm install node-red-contrib-presidio

## Presidio Setup :gear:
The subflow requires Microsoft Presidio services to be running on the host or a remote server that is reachable by Node-RED.
The documentation to install Presidio can be found [here](https://microsoft.github.io/presidio/installation/), we recommend using the Docker approach as follows:

```console
docker run -d -p 5001:3000 mcr.microsoft.com/presidio-analyzer:latest
docker run -d -p 5002:3000 mcr.microsoft.com/presidio-anonymizer:latest
```
Once the containers are deployed, use the health check to see that the Presidio services are reachable

- :information_source: **POST localhost:1880/HealthCheck**

![HealthCheck](https://github.com/Doth-J/node-red-contrib-presidio/blob/master/docs/HealthCheck.PNG)

* Health Check response payload:
![HealthCheckResponse](https://github.com/Doth-J/node-red-contrib-presidio/blob/master/docs/HealthCheckResponse.PNG)

## Analyzer API :toolbox:

- :information_source: **POST localhost:1880/Presidio**

The __data__ payload parameter must be a string and you must define the __function__ to ``analyze``.

### Analyzing PIIs :adult: :arrow_right:
* Setting the payload of the **Presidio Analysis** injector:

![Analysis1](https://github.com/Doth-J/node-red-contrib-presidio/blob/master/docs/Analysis1.PNG)

#### Analysis Result :receipt: :back:
* Analysis response payload:
![Analysis2](https://github.com/Doth-J/node-red-contrib-presidio/blob/master/docs/Analysis2.PNG)

---

## Anonymizer API :toolbox:
:warning: Refer to Presidio API documents [HERE](https://microsoft.github.io/presidio/api-docs/api-docs.html) 

- :information_source: **POST localhost:1880/Presidio**

The __data__ payload parameter must be a string, you must also define the __function__ to ``anonymize`` and  which  __action__ to use for the PIIs (``redact``,``replace``,``mask``,``hash``,``encrypt``).

### Hashing PIIs :adult: :receipt: :arrow_right:
* Setting the payload of the **Presidio Anonymization** injector: 
![Hash1](https://github.com/Doth-J/node-red-contrib-presidio/blob/master/docs/Hash1.PNG)

#### Hashing Response :receipt: :back:
* Hashing response payload:
![Hash2](https://github.com/Doth-J/node-red-contrib-presidio/blob/master/docs/Hash2.PNG)

---

### Encrypting PIIs :adult: :receipt: :arrow_right:
* Setting the payload of the **Presidio Anonymization** injector:
![Anonymize1](https://github.com/Doth-J/node-red-contrib-presidio/blob/master/docs/Anonymize1.PNG)

#### Encryption Response :receipt: :back:
* Encryption response payload:
![Anonymize2](https://github.com/Doth-J/node-red-contrib-presidio/blob/master/docs/Anonymize2.PNG)

---

### Decrypting PIIs :receipt: :arrow_right: 
* Setting the payload of the **Presidio Anonymization** injector:
![Deanonymize1](https://github.com/Doth-J/node-red-contrib-presidio/blob/master/docs/Deanonymize1.PNG)


#### Decryption Response :adult: :back:
* Decryption response payload:
![Deanonymize2](https://github.com/Doth-J/node-red-contrib-presidio/blob/master/docs/Deanonymize2.PNG)

 