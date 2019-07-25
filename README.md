## openmrs-docker
A docker env for OpneMRS.

### Setup
To bring up a local openmrs server:

```
git clone git@github.com:mddubey/openmrs-docker.git
cd openmrs-docker
sh rebuild.sh
```
It will take sometime to boot up. One way to figure out if the server is up to check output of status column in `docker ps`. The status should be `(healthy)`. Once the server is up, go to the link http://localhost:8080/openmrs.


### Configuration
* `omods` folder has been synced as `opnemrs_modules_directory`. Any omods put here will directly would be accessible by openmrs platform. The container needs to be restarted after any change to `omods` folder.
* Specifc `OWAs` needs to be added in `docker-compose.yml#volumes` section.
* `rebuild.sh` script will kill both containers, remove the volumes and restart the containers. The 2nd step when data persistance is needed.
* To start `openmrs` in debug mode, uncomment the `DEBUG:true` in `docker-compose.yml#openmrs-referenceapplication#environment` section. It will start the openmrs in debug mode(`no suspend`) and listen on port `1044`. The same port is being mapped on `1044` of `localhost`. `Intellij remote debugger` can be attached to `localhost:1044`.

### Resources
* [Github](https://github.com/openmrs/openmrs-module-basicmodule) repo for a sample openmrs module(omod).