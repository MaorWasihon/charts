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
go env spec , for each env set the name (as needed for the app) ,\
also add key the same name but in small letters . \
example: \
Adding enviorment variables ENV1,ENV2 .   


``` yaml
# YAML
envSecrets:
  - key: EXAMPLE_ENV
    value: "enter-value"
...
```

# 
## TLS CERTIFICATE 

To set the path for the tls cert and key . \
change the certhPath value. 
``` yaml
# YAML
tlsConfig: 
  certsPath: /mnt/tls
...
```

# 
## CONFIG MAP 
To set the path for the config files \
that needed , change the path value . 
* same as TLS cert
``` yaml
# YAML
configMap:
  path: "/etc/config"
  list: 
    - key: "property"
      value: "property-value"
  configFile: 
    create: true
    name: "file-name"
    data:
      - key: "key"
        value: "val"

...
```

# 
## CONFIG FILES 
To set the path for the config files \
that needed , change the path value . 
* same as TLS cert
``` yaml
# YAML
configMap:
  path: /etc/config
...
```