# Helm Charts (for) Home Use
Simple Helm Charts for Home Use. 

## TL;DR;
- Simple way of running a few containers in Kubernetes (K3S). 
- No Scaling, no RBAC, no service mesh
- All of them are linux/arm(V7) compatible

## Prerequisites
- Helm Version 3 required
- Traefik 2+ & CRD required (TODO: Include as chart)
  
## ¨Features¨

### **Self Contained Repo**
Apart from the docer images no charts have dependencies outside of this repository.


### **KISS** - Keep it stupid simple
These charts are simple. It is not recomended to deploy these in a corporate environment. 


### **RBAC** - No Service Accounts
The charts are ment to be deployed on a home server or raspberry PI. They likely end up in the same namespace and the default service acount is fine for them so they do not include one.


### **DRY** - Dont repeat yourself
The charts use a library chart called `baseChart`. This includes most of the manifest structures.


### **PI** - Fit for raspberry PI
As many home users I am running charts on a raspberry pi. Therefore the docker images used by these charts are able to run on `linux/arm(V7)`


## Installation
As usual with helm charts you can just clone the repo and run helm install.  
- As the charts usualy do not include a namespace you should provide one in the helm command.  
- Also most of the charts have opinionated defaults, but you are expected to check them and provide a file with your custom values.

So installing a chart could look like this:
```CLI
  helm install -n <namespace> -f <custom_values.yaml> <release> <chart_dir>
```

### Naming Prefix
By default the charts will also not use the release prefix. If you wish to have a prefix set the value
```yaml
  usePrefix: true 
```

### Values
For simplicity you can define the custom values in a file that you pass to helm like above. The file will have to look like this:
```yaml
  usePrefix: true

  env:
    SOME_ENV_VARIABLE: value
```
Check the `values.yaml` files for the values to overwrite. 

