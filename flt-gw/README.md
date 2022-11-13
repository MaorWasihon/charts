# FLT-GateWay Chart 


## Developers values
# 
All the values that need to be modify by the FLT-GW developers are ,\
Inside the values.yaml file under 'DEVELOPRS-SECTION' comment .

``` yaml
# ------- DEVELOPERS-SECTION ------------
```


# 

## ENV
For adding enviorment variables for FLT-GW 
go env spec , for each env set the name (as needed for the app) . \
example: \
Adding enviorment variables 'KAFKA_URL'.   


``` yaml
# YAML
envSecrets:
  - key: KAFKA_URL
    value: "https://example.com"
# - key: ENV
#   value: ENV_VAL
...
```

result inside app : 

```sh
env
KAFKA_URL="https://example.com"
```

# 
## CONFIG MAP 
You can create files that will mounted to app environment.  
``` yaml
# YAML
configMap:
  path: /etc/config
  list: 
    - key: "name"
      value: "content" 
  create: true
  files: 
    - name: "TLS_CERT"
      data: | 
        ---- CERT ----
    - name: "TLS_KEY"
      data: | 
        ---- KEY ----

...
```

For changing the dir for mount change path value . 
``` yaml
# YAML
configMap:
  path: /etc/config
```
For adding files with one-line string under 'list'\
scope enter key, value pairs . 
* key = name-of-file , value=content-of-file
``` yaml
configMap:
  path: /etc/config
  list: 
    - key: "name"
      value: "content" 
```

result inside app environment :
```sh
ls /etc/config
name
cat name
content
```
For adding TLS env and files that contains more \
then one-line string , set configMap.create: true. 
```yaml
#YAML
configMap:
  path: /etc/config
  list: 
    - key: "name"
      value: "content" 
  create: true
```
At files spec specify tha name of the and data \ 
* data = file-content . \
example: 
```yaml
#YAML
configMap:
  path: /etc/config
  list: 
    - key: "name"
      value: "content" 
  create: true
  files: 
    - name: "TLS_CERT"
      data: | 
        -----BEGIN CERTIFICATE-----
        ---------------------------------
        -------------------------------
        ------------------------------
        -----END CERTIFICATE-----
    - name: "TLS_KEY"
      data: | 
        -----BEGIN RSA PRIVATE KEY-----
        ------------------------------------
        ---------------------------------
        ---------------------------------------
        -----END RSA PRIVATE KEY-----
```