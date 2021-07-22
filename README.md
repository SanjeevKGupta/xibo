## Xibo - A digital signage CMS application 

This example project uses `docker-compose.yml` file from https://github.com/xibosignage/xibo-docker and creates IEAM deployment files so that application can be deployed on IEAM. Application migration from `docker-compose.yml` was done manually and it was not that difficult.

### Notes

IEAM uses [semver](https://semver.org) naming scheme for releases. I re-tagged and pushed cms, xmr and ianw images into another repository to make the service publishing possible essier in IEAM.

### Setup
Setup following ENV variables to publish the service, pattern and register the edge node.

```
#### Enviornment variables EDGE_OWNER, EDGE_DEPLOY to identify service. Change as needed to organize your service, policy names etc.
export EDGE_OWNER=<change-as-needed> e.g sg.edge           
export EDGE_DEPLOY=<change-as-needed> e.g example.xibo 

#### Specify your docker login name
export DOCKER_BASE=<change-as-needed> e.g edgedock
    
# Sets the root of the bind volume. Create this before running the application with 777 access
export APP_BIND_HORIZON_DIR=/var/local/horizon
export MYSQL_PASSWORD=<specify-a-good-password>
```

### Publish services to IEAM exchange
```
cd publish
make
```

### Register edge node 
```
cd register
./register.sh
```
### Test and Verify
Access the deployed application as `http:<ip-address-of-your-edge-node>`

### Reference and acknowledgments:
https://xibo.org.uk/docs/setup/xibo-cms-with-docker-on-ubuntu-18-04

